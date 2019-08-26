## case1(요즘)
~~~js
const TodoListTemplate = ({form. childeren}) => {
    return (
        
    );
}

export default TodoListTemplate;
~~~

## case2
~~~js
import {Component} from 'react;

class TodoListTemplate extends Components {

    state

    ComponentsdidMount() {
    
    }
  render() {
    return (
        <>
        asdfasdfasdfsdfasdfasdfasdfas
        </>
    )
  }
}
~~~
class는 state를 사용할 수 있음
ComponentdidMount
hooks..??


함수형(const)으로 하는 이유
- 성능상 이유

#### var, let, const
const는 뒤에 변할 수 없는 값이 들어감!
하지만 뒤에 함수를 쓰면..?(함수는 자주변함)

원시값(<->참조값)
-->괜찮음!! 참조값으로 저장이 되기때문에 경로(위치)만 저장됨!따라서 그 값이 바껴도 상관없음!!!

## case1
~~~js
const TodoListTemplate = ({form, childeren}) => {

  return ();
};  
~~~
## case2
~~~js
const TodoListTemplate = (props) => {

  const { form, children } = this.props
  return ();
};
~~~
~~~js
const { form} = this.props //비구조 할당을 이용하기 위해서 {}사용!
const [ form] = this.props //비구조할당을 배열로써 이용하기 위해서 []사용!
~~~
~~~js
  const {A} = this.props.ex1.form
  ex1 = {
      form : [
        A :1
        B :2
      ],
      title : 222
  }
  ~~~


~~~js
class App extends Component {
  render(){
    return (
      <>
        // 첫번째case
        <TodoListTemplate form="">
          여기 템플릿과 탬플릿사이에 이 공간이 바로 children 입니다.
          <todolist/>
        </TodoListTemplate>

        // 두번째case
        <TodoListTemplate/>
      </>
    );
  }
}
~~~
첫번째case는 <>~</>안에 하위컴포넌트를 넣을 수 있음!

~~~js
    <List onClick={함수1}/> //컴포넌트의 이벤트 처리기는 없음! 그저 프롭스일 뿐!!
    <input onClick={함수2}/> //html태그 안에서는 이벤트처리기로 인식함!
~~~

### css_flex
~~~css
.form input {
  flex: 1; /* 버튼을 뺀 빈 공간을 모두 채워줍니다 */
  font-size: 1.25rem;
  outline: none;
  border: none;
  border-bottom: 1px solid #c5f6fa;
}
~~~
flex에서 1은 100%를 의미
cursor: pointer 는 그 위치에서 커서모양이 포인터(손가락모양)으로 바뀜


~~~js
    return (
      <>
        <TodoListTemplate form={<Form/>}>
          여기 템플릿과 탬플릿사이에 이 공간이 바로 children 입니다.
        </TodoListTemplate>
      </>
    );
~~~
둘 사이에 실선을 넣고자 한다면 위의 경우에는 todolistTemplate에 그 사이에 css적용시키면 되고
아래의 경우에는 그 하위의 컴포넌트 form 에서 css적용시켜야한다

~~~js
render(){
    return (
      <>
        <TodoListTemplate>
          <Form/>
          여기 템플릿과 탬플릿사이에 이 공간이 바로 children 입니다.
        </TodoListTemplate>
      </>
    );
  }
  ~~~

  toggle???

  ~~~js
      return (
      <div className="todo-item" onClick={() => onToggle(id)}>
        {/* 1 */}
        <div className="remove" onClick={(e) => {
          e.stopPropagation();
          onRemove(id)
        }}>
          &times;
        </div>


        {/* 2 */}
        <div className={`todo-text ${checked && 'checked'}`}>
          <div>{text}</div>
        </div>
        
        {
          checked && (<div className="check-mark">&#x2713;</div>)
        }
      </div>
    );
    ~~~

    onclick이 자식에도 부모에도 있다 --> 두개가 같이 된다..
    e.stopPropagation(); 을 적어주면, 이것을 포함한 부분의 onclick 실행됨
    --> 여기서는 onremove만 실행되고 ontoggle은 실행되지 않음!

~~~js
    //첫번째
    <div className="todo-item" onClick={() => onToggle(id)}>
    //두번째
    <div className="todo-item" onClick={onToggle(id)}>
~~~
두번째로 쓴다면 이 페이지를 렌더링 할때 저 코드를 읽자마자 ontoggle함수가 실행이 되버린다. 즉 클릭되지도 않았는데 ontoggle이 실행되버린거지!
하지만 첫번째 경우에는 onclick(행위)가 일어나면 실행된다.
~~~js
    onClick={() => onToggle(id)}
    와

    function onClick = () => {
        onToggle(id)
    }
    은 같은말!! // 클릭이 됬을때 ontoggle실햄됨
~~~

엔티티숫자!
보강표현법 
 - `여기안에는 문자로 인식`
 - ${여기안에는 js문법으로 인식}

 #### checked && 'checked'
 checked가 트루라면 &&뒤의 것에 의해 결정!-->checked되어지면 'checked'글자가 나옴!

 **checked ? 'checked' : ''** 와 같은말!

 #### transition: all 0.15s;
 모든 행동(ex : hover) 이 완료되기까지의 시간을 정해줌!
 0s는 커서를 올리자마자 바뀌지만 1s는 서서히 바뀌다가 1초가 지났을때는 완료!

 #### ref??input태그 구별해주는것!??

 #### 배열추가
 concat : 추가한 것에 대해서 복사본을 만듬!
 push : 원본이 수정됨

####
 ~~~js
         const todoList = todos.map(
            ({id, text, checked}) => (
                <TodoItem
                    id={id}
                    text={text}
                    checked={checked}
                    onToggle={onToggle}
                    onRemove={onRemove}
                    key={id}
                />
            )
        )
~~~
key는 꼭 써줘야함!리액트가 인식할 수 있게 하는 거!??

####
const index = todos.findIndex(todo => todo.id === id);
findIndex괄호안에 있는 조건이 맞을때의 인택스

####

[a,...todos] // 에서 ...todos는 a를 제외한 나머지
[...todos]  따라서 왼쪽의 경우에는 todos 전체!를 의미(복사의 개념도 있음)