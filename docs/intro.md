[todo mvc 예제를](https://kr.vuejs.org/v2/examples/todomvc.html) 통해 Vue.js 기본 적인 개념을 파악하고,
단일 컴포넌트로 되어 있는 예제 프로그램을
부모 자식간의 컴포넌트 구조로 변경하면서 컴포넌트간 통신에 대해서도 파악해본다.

* [VueCLI](https://cli.vuejs.org/) 혹은 webpack을 통한 [SFC](https://kr.vuejs.org/v2/guide/single-file-components.html) 개발 환경이라 가정한다.

* 개념에 대한 내용은 [공식 Document(한글번역판)](https://kr.vuejs.org/v2/guide/)을 참고 한다.

### 예제에 사용된 기본 개념 파악하기

----

**[Vue 인스턴스](https://kr.vuejs.org/v2/guide/instance.html#Vue-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EB%A7%8C%EB%93%A4%EA%B8%B0)**
    vue의 다양한 option을 가진 객체
    
**[Vue 인스턴스 라이프 사이클](https://kr.vuejs.org/v2/guide/instance.html#%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EB%9D%BC%EC%9D%B4%ED%94%84%EC%82%AC%EC%9D%B4%ED%81%B4-%ED%9B%85)**

-----
<details>
        <summary> template</summary>

* [템플릿 문법](https://kr.vuejs.org/v2/guide/syntax.html)
* [보간법](https://kr.vuejs.org/v2/guide/syntax.html#%EB%B3%B4%EA%B0%84%EB%B2%95-Interpolation)
    {{ data }}
    가장 기본적인 데이터 바인딩 형태
    javascript 표현식 사용 가능 ( {{ number + 1 }}, {{ ok ? 'YES' : 'NO' }} )
* [디렉티브](https://kr.vuejs.org/v2/guide/syntax.html#%EB%94%94%EB%A0%89%ED%8B%B0%EB%B8%8C)
    tag의 속성 중 v- 시작하는 Vue.js 문법
    * [v-model](https://kr.vuejs.org/v2/guide/forms.html)
        input, textarea 엘리먼트 vue 인스턴스 data와 양방향 바인딩
    * [v-on](https://kr.vuejs.org/v2/guide/events.html)
        dom 이벤트 리스너
        jQuery에서 $('element').on('event', funtion(){...})
    * [v-bind](https://kr.vuejs.org/v2/guide/class-and-style.html)
        class, style을 동적으로 바인딩
        또는 tag 속성을 동적으로 바인딩
    * [v-for](https://kr.vuejs.org/v2/guide/list.html)
        숫자(range), 배열, 객체를 반복적으로 랜더링시에 사용
    * [custorm 디렉티브](https://kr.vuejs.org/v2/guide/custom-directive.html)
        todo item을 보여주는 input 속성 중 v-todo-focus="todo === editedTodo" 존재한다.    
        공식문서에 존재하지 않는 디렉티브이다. 하단의 javascript에서 커스텀하게 디렉티브를 선언한 것을 볼 수 있다.
        ```javascript
        directives: {
            'todo-focus': function(el, binding) {
                if (binding.value) {
                    el.focus();
                }
            },
        },
        ```
    * [v-if](https://kr.vuejs.org/v2/guide/conditional.html#v-if), [v-show](https://kr.vuejs.org/v2/guide/conditional.html#v-show)
        화면에서 엘리먼트롤 조건부로 표시
</details>

----

\<script>
* [data](https://kr.vuejs.org/v2/guide/instance.html#%EC%86%8D%EC%84%B1%EA%B3%BC-%EB%A9%94%EC%86%8C%EB%93%9C)
    반응형 프로그램(reactivity system)을 만들기 위한 기본 요소
    > When a Vue instance is created, it adds all the properties found in its data object to Vue’s reactivity system. When the values of those properties change, the view will “react”, updating to match the new values. [english document](https://vuejs.org/v2/guide/instance.html#Data-and-Methods)
    * [Vue의 반응형에 대해 깊이 알아보기](https://kr.vuejs.org/v2/guide/reactivity.html)
* [computed](https://kr.vuejs.org/v2/guide/computed.html)
    계산된 속성
* [watch](https://kr.vuejs.org/v2/guide/computed.html#watch-%EC%86%8D%EC%84%B1)
    data의 변경에 반응
* [filters](https://kr.vuejs.org/v2/guide/filters.html)
    텍스트 형식화
* [methods](https://kr.vuejs.org/v2/api/#methods)
    Vue 인스턴스에 추가할 메소드
\</script>
