# 2019.12.05 목요일

### :book: 리액트를 다루는 기술(개정판)
- 6장. 컴포넌트 반복
    - map, filter 사용법에 대한 내용.
    - function 형식으로 되어 있는 예제를 **class 형식**으로 변경해서 구현해 봄.
    ```javascript
    import React, { Component } from 'react';

    class Counter extends Component {
        state = {
            names: [
                { id: 1, text: '눈사람' },
                { id: 2, text: '얼음' },
                { id: 3, text: '눈' },
                { id: 4, text: '바람' }
            ],
            nextId: 0,
            inputText: ''
        }

        onClick = () => {
            const { names, nextId, inputText } = this.state;

            const newNextId = (nextId !== 0) ? nextId : names[names.length - 1].id + 1;
            const newValue = [...names, {
                id: newNextId,
                text: inputText
            }];

            this.setState({ names: newValue, inputText: '', nextId: newNextId + 1 });
        }

        onChange = (e) => {
            this.setState({ inputText: e.target.value });
        }

        onRemove = (id) => {
            const filterNames = this.state.names.filter(name => name.id !== id);
            this.setState({
                names: filterNames
            })
        }

        render() {
            const { names } = this.state;

            return (
                <>

                    <input onChange={this.onChange} />
                    <button onClick={this.onClick}>추가</button>
                    <ul>{names.map(name => <li key={name.id} onDoubleClick={() => this.onRemove(name.id)}>{name.text}</li>)}</ul>
                </>
            );
        }
    }

    export default Counter;
    ```


- 7장. 컴포넌트의 라이프사이클 메서드
    - 클래스형태의 컴포넌트에서만 사용할 수 있다.(함수형 컴포넌트에서는 Hook를 이용해서 처리 가능)
    
    - **mounting**
        - constructor()
        - _staic_ getDerivedStateFromProps()
        - render()
        - componentDidMount()
    - **updating**
        - _staic_ getDerivedStateFromProps()
        - shouldComponentUpdate() : false 작업취소
        - render()
        - getSnapshotBeforeUpdate()
        - componentDidUpdate()
        - 예) state변경(setState)가 발생하면 render()를 rendering하고 componentDidUpdate()를 발생한다
    - **unmounting**
        - componentWillUnmount()


- 8장. Hook
    - useState
    - useEffect