# what-is-react

다음은 노션에 정리 된 내용을 readme에 작성한 내용입니다
[원본 노션 링크](https://www.notion.so/REACT-82a9a44bed6c443f93418508e17c120e)
_완성후 파일 첨부 예정!_

<details><summary>error or issues</summary>
    
    Warning: ReactDOM.render is no longer supported in React 18. Use createRoot instead. Until you switch to the new API, your app will behave as if it's running React 17. Learn more: [https://reactjs.org/link/switch-to-createroot](https://reactjs.org/link/switch-to-createroot)
    
    →  react version issue, change version from 18 to 17
    
    ```jsx
    <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    ```
</details>

# Ch1. React Getting Started

## React Concept

### 1. Angular vs React vs Vue

1. [Angular](https://angular.io/) 
    1. cross platform
    2. 거의 모든 기능이 하나로 이루고 있다   [출처](https://angular.io/features)
2. Vue
    1. the progressive javascript framework ⇒ 두 마리 토끼
3. React
    1. javascript library for building user interfaces
    
    angular full framework react library vue는 둘다
    

### 2. Component Based Development

component: 기존의 css tag처럼 내가 만든 컴포넌트 사용 가능

문서(html), 스타일(css), 동작(js)를 합쳐서 내가 만든 일종의 태그

ex) 

<내가 지은 이름1 name=”Mark” >

<내가 지은 이름 prop={false}>내용</내가 지은 이름> // prop: property 약자

![Component Tree](https://www.notion.so/REACT-82a9a44bed6c443f93418508e17c120e#623e1dce08454e02b0cc5bbb55107983)

### 3. ⭐️ Virtual Dom → Dom을 다루는 일을 react에 위임

*DOM(Document Object Model)

- DOM을 직접 제어하는 경우: 바뀐 부분만 정확히 바꿔야 한다
- DOM을 직접 제어하지 않는 경우: 가상의 돔 트리를 사용해서 이전 상태와 이후 상태를 비교하여 바뀐 부분을 찾아내서 자동으로 바꾼다

### JSX (templates이 아니라 순수한 JS로 transpile 되는 문법)

### CSR(Client Side Rendering)

- 빈 html 다운 → html 안에 있는 JS → react web/app을 실행 → componet 가 그려지면 보여짐
- JS가 전부 다운로드 되어 리액트 어플리케이션이 정상 실행 되기 전까지는 화면이 보이지 않음
- JS가 전부 다운로드 되어 리액트 어플리케이션이 정상 실행된 후, 화면이 보이면서 유저가 인터렉션 가능

### SSR(Server Side Rendering)
- 사실 상 동작의 차이는 없으나 SSR 할 때 html rendering 후 기능은 동작하지 않아도 보여지는 것은 보여진다
- JS가 전부 다운로드 되지 않아도 일단 화면은 보이지만 유저가 사용할 수는 없음
- JS가 전부 다운로드 되어 리액트 어플리케이션이 정상 실행된 후, 유저가 사용 가능
-----
## 개발 환경 세팅

### Node.js  
[설치](https://nodejs.org/ko/)

LTS: 안정적인 환경

nvm: https://github.com/nvm-sh/nvm

### Browser(Chrome), Git, Vscode

## React 라이브러리

```js
import ReactDom from 'react-dom' // React component => HTMLElement 연결하기
import React from 'react' // React component 만들기
```

- Dom.render(); : JS, JSX 문법을 사용한 React 컴포넌트 ⇒ HTMLElement로 연결해주는 역할

```js
// HTMLElement에 react component를 그려라 (render)
ReactDom.render (
	<HelloMessage name="Taylor" />
	document.getElementById('hello-example')
);
```

```js
// 하나의 component
class HelloMessage extends React.Component {
	render() {
		return (
			<div>
				Hello {this.props.name} //Taylor
			</div>
		);
	}
}
```

- React component 만들기
    - CDN을 통한 react library 사용
        1. nvm init -y
        2. npx server → local host server 실행
        3. index.html  파일 생성
            1. [https://ko.reactjs.org/docs/cdn-links.html](https://ko.reactjs.org/docs/cdn-links.html) ⇒ cdn을 가져와서 react 라이브러리로 사용 가능
            
            ```jsx
            <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
            <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
            // development ver *product용도 있음
            ```
            
            b.
            
            ```html
            <!DOCTYPE html>
            <html lang="en">
            <head>
                <meta charset="UTF-8">
                <meta http-equiv="X-UA-Compatible" content="IE=edge">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <title>Example</title>
            </head>
            <body>
                <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
                <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
                <script type="text/javascript">
                    console.log(typeof(React)); //object 
                    console.log(typeof(ReactDOM)); //object
                </script> 
            </body>
            </html>
            ```
            
- 기존의 프론트는 html 로 구조를 만들고 css로 style을 입히고 javascript로 dom을 조종하였다

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>React Example</title>

    <style>
        * {
            margin: 0;
            border: 0;
            padding: 0;
        }
        #root p {
            colro: white;
            font-size: 20px;
            background-color: green;
            text-align: center;
            width:200px;
        }
        #btn_plus {
            background-color: red;
            border: 2px solid #000000;
            font-size: 15px;
            width: 200px;
        }

    </style>
</head>
<body>
    <div id="root"></div>
    <button id="btn_plus">+</button>
		<!-- Change react@18 -> react@17 -->
    <script crossorigin src="https://unpkg.com/react@18/umd/react.development.js"></script>
    <script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
    <script type="text/javascript">
        // console.log(typeof(React));
        // console.log(typeof(ReactDOM));
        

        const root = document.querySelector("#root");
        const btn_plus = document.querySelector("#btn_plus");

        let i = 0;

        root.innerHTML = "<p>init : 0</p>";

        btn_plus.addEventListener("click", () => {
            root.innerHTML = `<p>init : ${++i}</p>`
        });
    </script> 
</body>
</html>
```

- render 사용

```html
<script type="text/javascript">
    const component = {
        message: 'init',
        count: 0,
        render() {
            return `<p>${this.message} : ${this.count}</p>`;
        }
    };

    function render(rootElement, component) {
        rootElement.innerHTML = component.render();
    }
    
    // initialization
    render(document.querySelector('#root'), component);
    

    document.querySelector('#btn_plus').addEventListener('click', () => {
        component.messgae = 'update';
        component.count = component.count + 1;

        render(document.querySelector("#root"), component);
    });
</script>
```

- react 사용

```html
<script type="text/javascript">
    // <p>props의 message : props의 count</p>
    const Component = props => {
        // 꼭 react elementf로 return 되어야 한다
        return React.createElement('p', null, `${props.message} : ${props.count}`);
    }

    ReactDOM.render(/* 리엑트 컴포넌트, 컴포넌트가 그려질 실제 DOM */
        // react component를 사용하기 위해 createElement
        React.createElement(Component, { message: "init", count: 0 }, null),
        document.querySelector('#root')
    );

    document.querySelector("#btn_plus").addEventListener("click", () => {
        ReactDOM.render(/*React Component Here*/
            React.createElement(
                Component,
                { message: "init", count: 10 },
                null),
            document.querySelector('#root')
        );
    });
</script>
```

---

# Ch2. React Component

## React Component 만드는 법

- Hooks 이전
    - 컴포턴트 내부에 유지해야할 상태가 있다면 → class
    - 없다면 → 라이프사이클을 이용 해야 한다면 → class , 아니라면 → function
- Hooks 이후 : class, function
1. Class Component
    1. class
    
    ```html
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    // import React from 'react'; // javascript 
    <script type="text/babel">
        // 정의
        class ClassComponent extends React.Component {
            render() {
                return (<div>Hello</div>);
            }
        }
        // 사용
        // <ClassComponent /> 
        ReactDOM.render(
            <ClassComponent />,
            document.querySelector("#root")
        );
    </script>
    ```
    
    b. function
    
    ```html
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script type="text/babel">
        // 정의 1
        // function FunctionComponent() {
        //     return <div>Hello</div>;
        // }
        
        // 정의 2
        const FunctionComponent = () => <div>Hello</div>;
    
        // 사용
        ReactDOM.render(<FunctionComponent />, document.querySelector("#root"))
    </script>
    ```
    

## React.createElement 로 컴포넌트 만들기

```html
<!-- createElement 형태
React.createElement(
    type, // 문자열 태그 이름 | 리액트 컴포넌트 | React.Fragment
    [props], // 리액트 컴포넌트에 넣어주는 데이터 객체
    [...children] // 자식으로 넣어주는 요소들
);
-->

<!-- 1. 문자열 태그 이름 type -->
<script type="text/javascript">
		// <h1></h1>와 같음
		ReactDOM.render(
		    React.createElement("h1", null, `type이 이 "문자열 태그 이름" 입니다.`),
		    document.querySelector("#root")
		);
</script>

<!-- 2. 리엑트 컴포넌트 type -->
<script type="text/javascript">
		const Component = () => {
            return React.createElement(
                "p",
                null,
                `type 이 "React 컴포넌트" 입니다.`
            )
        };

		// <Component></Component> => <Component /> -> <p>type 이 "React 컴포넌트" 입니다.</p>"
		ReactDOM.render(
		    React.createElement(Component, null, null),
		    document.querySelector("#root")
		);
</script>

<!-- 3. React.Fragment -->
<script type="text/javascript">
		ReactDOM.render(
        React.createElement(
            React.Fragment,
            null, 
            `type is React.Fragment`
            // 이렇게 하면 root div 아래에 여러가지 요소를 넣을 수 있다 (배열 형태로 추가 됨)
        ),
        document.querySelector('#root')
    );
</script>

<!-- 4. 복잡한 구조 -->
<script type="text/javascript">
		// Target:
    //     <div>
    //         <h1>Topic</h1>
    //         <ul>
    //             <li>React</li>
    //             <li>Vue</li>
    //         </ul>
    //     </div>
		ReactDom.render(
        React.createElement(
            "div",
            null,
            React.createElement("h1", null, "주제"),
            React.createElement(
                "ul",
                null,
                React.createElement("li", null, "React"),
                React.createElement("li", null, "Vue")
            )
        ),
        document.querySelector("#root")
    )
</script>
```

## JSX

babel: [https://babeljs.io/](https://babeljs.io/)

우리가 작성한 어떤 코드를 순수하게 실행할 수 있는 자바스크립트로 바꿔야 한다

babel 은 이전 버전 혹은 쓰이지 않는 코드를 작성하여도 현재 사용가능한(실행가능한) 코드로 바꿔준다

- 사용

```html
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
<script type="text/babel">
		ReactDom.render(
        <div>
            <h1>Topic</h1>
            <ul>
                <li>React</li>
                <li>Vue</li>
            </ul>
        </div>
    )
</script>
```

- 왜 JSX를 쓰나요?
    - 가독성
    - 컴파일 과정에서 문법적 오류를 찾기 쉬움 (엄격한 기준)
    
- 문법
    - 최상위 요소가 하나
    - 최상위 요소를 return 하는 경우 ()로 감싸야 한다
    - 자식들을 바로 rendering 하고 싶으면 <>자식들</> 사용 ⇒ Fragment
    - javascript 표현식(elements)을 사용하려면 {표현식(elements)}를 이용
    - if 문 x
        - 삼항 연산자 혹은 && 를 사용
    - style 을 이용해 인라인 스타일링 가능
    - class 대신 className을 사용해 class 적용
    - 자식요소가 있으면 꼭 닫아야 하고 없으면 열면서 닫아야 한다
        - <p></p>
        - <img />

## Props 와 State

- Props와 State
    - Props는 컴포넌트 외부에서 컴포넌트에게 주는 데이터
    - State는 컴포넌트 내부에서 변경할 수 있는 데이터
        - 둘 다 변경이 발생하면 렌더가 다시 일어날 수 있다
- Render 함수
    - Props와 State를 바탕으로 컴포넌트를 그린다
    - 그리고 Props, State가 변경되면 컴포넌트를 다시 그린다
    - 컴포넌트를 그리는 방법을 기술하는 함수가 Render 함수
1. function component

```html
<script type="text/babel">
    function Component(props) {
        return (
            <div>
                <h1>{props.message} 이것은 함수로 만든 컴포넌트 입니다.</h1>
            </div>
        );
    }
    ReactDOM.render(
        <Component message="안녕하세요!!!" />,
        document.querySelector("#root")
    );
</script>
```

1. class component - Props

```jsx
class Component extends React.Component {
    render() {
        return (
            <div>
                <h1>{this.props.message}</h1>
                {"Helloooooooo"}
            </div>
        )
    }
    static defaultProps = {
        message: "Default",
    };
}
// Class may have 2 ways of defining default component
// method 1
// Component.defaultProps = {
//     message: "Default Value",
// };

// Method 2
// !!within the class component:
// static defaultProps = {
//     message: "Default",
// };
ReactDOM.render(<Component />, document.querySelector("#root"));
```

1. class component - State

```jsx
class Component extends React.Component {
    state = {
        count: 0,
    };

    render() {
        return (
            <div>
                <h1>{this.props.message}</h1>
                {"Helloooooooo"}
                <p>{this.state.count}</p>
            </div>
            
        )
    }
    static defaultProps = {
        message: "Default",
    };
}
ReactDOM.render(<Component />, document.querySelector("#root"));
```

- State 초기화
    1. 좀 더 편함
    
    ```jsx
    state = {
    	count: 0,
    }
    ```
    
    1. 이 방법을 써야 할 때도 있다
    
    ```jsx
    constructor(props) {
    	super(props);
    	
    	this.state = { count: 0};
    }
    ```
    
- state를 변경할 때는 규칙이 있다.
    1. setState
    
    ```jsx
    this.setState({
        count: this.state.count + 1,
    })
    ```
    
    1. previous state 값을 new state 값으로 바꿈
    
    ```jsx
    this.setState((previousState) => {
    		const newState = { count: previousState.count + 1 }
    		return newState;
    });
    ```

    ## Event Handling

    - HTML DOM에 클릭하면 이벤트가 발생하고, 그 이벤트를 처리 할 수 있어야 한다
    - JSX에 이벤트를 설정할 수 있다 ⇒ 이벤트 처리하는 부분이 props로 들어가서 실제 Element이면 실제 Element에서 이벤트 발생
    - 규칙
        - camelCase로만 사용할 수 있다 * onClick, onMouseEnter
        - 이벤터에 연결된 자바스크립트 코드는 함수 * 이벤트={함수}
        - 실제 DOM 요소들에만 사용 가능
            - 리엑트 컴포넌트에 사용하면 그냥 props로 전달
    1. 기본형 - function 

    ```jsx
    function Component() {
        return (
            <div>
                <button onClick={() => {
                    console.log('clicked')
                }}>
                    클릭
                </button>
            </div>
        );
    }
    ReactDOM.render(<Component />, document.querySelector('#root'))
    ```

    1. 기본형 - class

    ```jsx
    class Component extends React.Component {
        state = {
            count: 0,
        };
        render() {
            return (
                <div>
                    <p>{this.state.count}</p>
                    <button onClick={() => {
                        console.log('clicked')
                        this.setState((state) => ({ ...state, count: state.count + 1 }));
                    }}>
                        클릭
                    </button>
                </div>
            );
        }
    }
    ReactDOM.render(<Component />, document.querySelector('#root'))
    ```

    1. 함수 따로 빼서 쓰기

    ```jsx
    class Component extends React.Component {
            state = {
                count: 0,
            };
            // 함수 따로 빼서 쓰기 1) constructor를 만들어서 binding
            // constructor(props) {
            //     super(props);
            //     this.click = this.click.bind(this);
            // }
            render() {
                return (
                    <div>
                        <p>{this.state.count}</p>
                        <button onClick={this.click}>
                            클릭
                        </button>
                    </div>
                );
            }
            // 이렇게 따로 빼기만 하면 setState undefined 에러 발생
            // click() {
            //     console.log('clicked')
            //     this.setState((state) => ({ ...state, count: state.count + 1 }));
            // }
            // 함수 따로 빼서 쓰기 2) using arrow function
            click = () => {
                console.log('clicked')
                this.setState((state) => ({ ...state, count: state.count + 1 }));
            }
            
        }
        ReactDOM.render(<Component />, document.querySelector('#root'))
    </script>
    ```

    ## Component Lifecycle (< v16.3 )

    - lifecycle: 리엑트 컴포넌트의 탄생부터 죽음까지 (브라우저에서 그려지는 순간부터 사라지는 순간까지)
    - 여러 지점에서 개발자가 작업이 가능하도록 method를 overiding 할 수 있게 해준다
    - Declarative : 탄생부터 죽음까지 순간 순간을 선언적으로 표현 해놓으면 컴포넌트가 해당 상황이 되면 그 함수를 실행시킨다
        - Initalization: constructor 가 불리면서 초기값(props, state) 세팅
        - Mounting: render 직전 - render - render 직후 // 여기까지 그려지는 단계
        - Updation: 상태 변경
        - Unmounting: 컴포넌트 종료

    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/78ddc565-36d4-4a5c-80c8-c1cb30e8d481/Untitled.png)

    - warning
        
        react-dom.development.js:61 Warning: componentWillMount has been renamed, and is not recommended for use. See [https://reactjs.org/link/unsafe-component-lifecycles](https://reactjs.org/link/unsafe-component-lifecycles) for details.
        
        v16.3 이하에서 사용 가능하지만 곧 없어질 것을 경고
        
    1. componentWillReceiveProps
        - props를 새로 지정했을 때 바로 호출됨
        - state의 변경에 반응하지 않는다
            - props의 값에 따라 state를 변경해야 한다면, setState 를 이용해야 한다 → 다음 이벤트로 각각 가는 것이 아니라 한번에 변경된다
    2. shouldComponentUpdate
        - props나 state 둘 중 하나가 변경되거나 둘다 변경되도 호출된다
        - newProps와 newState를 인자로 한다
        - return type이 boolean이다 : true면 render, false면 render가 호출되지 않는다 (default는 true)
    3. componentWillUpdate
        - 컴포넌트가 재렌더링 되기 직전에 불린다
        - setState 사용 x
    4. componentDidUpdate
        - 컴포넌트가 재렌더링을 마치면 불린다 (렌더링 직후)
    5. code & 추가 설명
        
        ```html
        <script type="text/babel">
          class App extends React.Component {
                state = {
                    age: 39,
                };
                constructor(props) {
                    super(props);
                    console.log('constructor', props);
                }
                interval = null;
                render() {
                    console.log('render');
                    return (
                        <div>
                            <h2>
                                Hello {this.props.name} - {this.state.age}
                            </h2>
                        </div>
                    );
                };
        		    // component 마운트 & 생성
        		    // componentWillReceiveProps, shouldComponentUpdate, componentWillUpdate, render, componentDidUpdate
                componentWillMount() {
                    console.log('componentWillMount')
                }
                componentDidMount() {
                    console.log('componentDidMount')
        
                    this.interval = setInterval(() => {
                        // console.log("setInterval")
                        this.setState((state) => ({ ...state, age: state.age + 1 }))
                    }, 1000)
                }
                componentWillReceiveProps(nextProps) {
                    console.log('componentWillReceiveProps', nextProps);
                };
                shouldComponentUpdate(nextProps, nextState) {
                    console.log('shouldComponentUpdate', nextProps, nextState);
                    return true; // or false -> 다음 단계로 넘어가지 않음 (render가 되지 않아 화면이 그대로)
                }
                UNSAFE_componentWillUpdate(nextProps, nextState) {
                    console.log('componentWillUpdate', nextProps, nextState);
                }
                //render
                componentDidUpdate(prevProps, prevState) {
                    console.log('componentDidUpdate', prevProps, prevState);
                }
                componentWillUnMount(){
                    // 호출해놓은 setInterval을 여기서 없애줘야함 -> 안그러면 어디선가 계속 돌아가고 있을 interval..
                    clearInterval(this.interval);
                }
            }
        
            ReactDOM.render(<App name="Mark" />, document.querySelector('#root'))
        </script>
        ```
        
        1. v 16.3 바뀐 component lifecycle
            - componentWillMount ⇒ getDerivedStateFromProps
            - render, componentDidMount
            - componentWillReceiveProps ⇒ getDerivedStateFromProps
            - shouldComponentUpdate, render
            - componentWillUpdate ⇒ getSnapshotBeforeUpdate : dom에 적용될 직후에 상태를 저장했따가
                - (dom에 적용)
            - componentDidUpdate : dom에 적용된 뒤 update
            - componentWillUnmount
            - code
                
                ```html
                <script type="text/babel">			
                	let i = 0;
                	
                	class App extends React.Component {
                        state = {list : []};
                
                        render(){
                            return (
                                <div id="list" style={{height: 100, overflow: "scroll", }}>
                                    {this.state.list.map((i) => {
                                        return <div>{i}</div>;
                                    })}
                                    </div>
                            );
                        }
                
                        componentDidMount(){
                            setInterval(() => {
                                this.setState((state) => ({
                                    list: [...state.list, i++],
                                }));
                            }, 1000)
                        }
                
                        // render 전의 scroll 상태와 후의 scroll 상태를 비교해서 맞춰주기
                        getSnapshotBeforeUpdate(prevProps, prevState) {
                            if(prevState.list.length === this.state.list.length) {
                                return null;
                            }
                            const list = document.querySelector('#list');
                            return list.scrollHeight - list.scrollTop; // 이 값을 snapshot으로 저장
                        }
                
                        componentDidUpdate(prevProps, prevState, snapshot) {
                            console.log(snapshot); // snapshot 잘 저장됐는지
                            // lenghth가 같으면 null 이 들어올 것이고 다르면 값이 들어올 것
                            if(snapshot === null){
                                false;
                            }
                            const list = document.querySelector('#list');
                            list.scrollTop = list.scrollHeight - snapshot;
                        } // 새로운 값이 생겨서 화면이 아래로 값이 생길 때 스크롤이 자동으로 내려가도록 만듦
                	}
                
                	ReactDOM.render(<App name="Mark" />, document.querySelector('#root'))
                </script>
                ```
                
        
        2. component 에러 캐치
        
        error boundary: 자기 자신한테 문제가 생기면 잡아내지 못한다는 단점이 있다 → 검사하고자 하는 객체를 자식으로 만들기
        
        [doc](https://ko.reactjs.org/docs/error-boundaries.html)
        
        ```jsx
        class App extends React.Component {
            state = {
                hssError: false
            };
            render() {
                if (this.state.hssError) {
                    return <div>예상치 못한 에러가 발생했다.</div>
                }
                return <WebService />;
            }
            componentDidCatch(error, info){
                this.setState({ hasError: true });
            }
        }
        ```
        

    ---

    # Ch3. Creating React Project

    ## Create React App

    - CRA (Create React App)

    [Create React App](https://create-react-app.dev/)

    [https://github.com/facebook/create-react-app](https://github.com/facebook/create-react-app)

    1. npx: npm 5.2.0 이상부터 함께 설치된 커맨드라인 명령어 

    ```
    // 프로젝트 생성 (node 프로젝트)
    npx create-react-app "name"
    ```

    1. package.json

    ```json
    "dependencies": {
        "@testing-library/jest-dom": "^5.16.4",
        "@testing-library/react": "^13.3.0",
        "@testing-library/user-event": "^13.5.0",
        "react": "^18.2.0",
        "react-dom": "^18.2.0",
        "react-scripts": "5.0.1", //react app , 이 버전은 프로젝트의 버전과 같다.
        "web-vitals": "^2.1.4"
      },
    ```

    1. production 모드는 코드가 작고 못생겼다(최적화 되어 있음) → 수정 x

    ```json
    npm run build // compile을 실행하고 source code를 작고 못생기게(?) 배포용(production용) 파일로 만들어준다 

    npm install -g serve // server 설치
    serve -s build // npm serve -s build -> 쓸 때마다 새로운 serve 사용
    ```

    1. testing: jest 기반

    ```json
    npm test
    ```

    1. eject : create react app에서 꺼내서 개발하겠다 → create react app에서 제공하지 않는 환경에서 개발하고 싶을 때, 꺼내서 자유롭게 쓸 때 
        - open source에서 잘 관리 되고 있는데 꺼내면 문제 생길 수 있음,, : 신중하게 결정해야함
        - eject 하고 나면 많은 dependency가 추가 되고 test 파일이 생긴다

    ```json
    npm run eject
    ```

    1. 정리
        - npm start
        - npm run build
        - npm test
        - npm run eject
    2. react project가 화면에 보여지는 원리

    - webpack: 우리가 작성한 파일(js, jsx, css, 파일 등) 확장자에 맞는 loader에 위임하는 것 → 이것이 CRA에 설정되어 있다