# Vue

https://vuejs.org/

![image-20221217162846197](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217162846197.png)

## Introduce

> *Vue (pronounced /vjuː/, like **view**) is a JavaScript  framework for building user interfaces. It builds on top of standard  HTML, CSS, and JavaScript and provides a declarative and component-based programming model that helps you efficiently develop user interfaces,  be they simple or complex.*
>
> ### Virtual DOM
>
> VueJS makes the use of virtual DOM, which is also used by other  frameworks such as React, Ember, etc. The changes are not made to the  DOM, instead a replica of the DOM is created which is present in the  form of JavaScript data structures. Whenever any changes are to be made, they are made to the JavaScript data structures and the latter is  compared with the original data structure. The final changes are then  updated to the real DOM, which the user will see changing. This is good  in terms of optimization, it is less expensive and the changes can be  made at a faster rate.
>
> ### Data Binding
>
> The data binding feature helps manipulate or assign values to HTML  attributes, change the style, assign classes with the help of binding  directive called **v-bind** available with VueJS.
>
> ### Components
>
> Components are one of the important features of VueJS that helps create custom elements, which can be reused in HTML.
>
> ### Event Handling
>
> **v-on** is the attribute added to the DOM elements to listen to the events in VueJS.
>
> ### Animation/Transition
>
> VueJS provides various ways to apply transition to HTML elements when they are added/updated or removed from the DOM. VueJS has a built-in  transition component that  needs to be wrapped around the element for  transition effect. We can easily add third party animation libraries and also add more interactivity to the interface.
>
> ### Computed Properties
>
> This is one of the important features of VueJS. It helps to listen to the changes made to the UI elements and performs the necessary  calculations. There is no need of additional coding for this.
>
> ### Templates
>
> VueJS provides HTML-based templates that bind the DOM with the Vue  instance data. Vue compiles the templates into virtual DOM Render  functions. We can make use of the template of the render functions and  to do so we have to replace the template with the render function.
>
> ### Directives
>
> VueJS has built-in directives such as v-if, v-else, v-show, v-on,  v-bind, and v-model, which are used to perform various actions on the  frontend.
>
> ### Watchers
>
> Watchers are applied to data that changes. For example, form input  elements. Here, we don’t have to add any additional events. Watcher  takes care of handling any data changes making the code simple and fast.
>
> ### Routing
>
> Navigation between pages is performed with the help of vue-router.
>
> ### Lightweight
>
> VueJS script is very lightweight and the performance is also very fast.
>
> ### Vue-CLI
>
> VueJS can be installed at the command line using the vue-cli command  line interface. It helps to build and compile the project easily using  vue-cli.

## Concepts

### MVVM

> 原理：https://segmentfault.com/a/1190000038375749

![image-20221217170114366](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217170114366.png)


> 想要Vue工作就必须`创建一个Vue实例`（并且要`传入配置对象`）
>
> **一个Vue实例只能binding一个容器**
>
> 真实`开发中只会有一个Vue实例`并且会配合着`组件`一起使用

> **MVVM**
>
> - M：模型（Model），data中的数据
> - V：视图（View），模板代码
> - VM：视图模型（ViewModel），Vue实例

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
    <!--1、导入Vue的包-->
    <script src="https://cdn.jsdelivr.net/npm/vue@2.6.10/dist/vue.js"></script>
</head>
<body>
<!--这个div区域就是MVVM中的 View-->
<div id="div1">
    {{name}}
</div>
</body>

<script>
    // 2、创建一个Vue的实例
    //new出来的对象就是MVVM中的 View Module（调度者）
    var myVue = new Vue({
        el: '#div1', //当前vue对象将接管上面的div1区域(容器和vue实例要一一对应)
        data: {//data就是MVVM中的 module
            name: 'smyhvae'
        }
    });
    myVue.$mount('#div1')//第二种挂载容器的写法{同el: '#div1',}（当前vue对象将接管上面的div1区域(容器和vue实例要一一对应)）
</script>
</html>
```

![image-20230312171603223](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230312171603223.png)

![image-20230312224053355](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230312224053355.png)

### Vue Lifecycle

![image-20230327112937791](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230327112937791.png)

![image-20230327125334668](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230327125334668.png)

### Options | Composition

> The Options API and the Composition API are two ways to define a component in Vue.js.
>
> 1. **Options API**: This is the standard way to create components in Vue.js. It's an object-based API where you define options 
>    (**data, methods, computed properties, lifecycle hooks**, etc.)
>     inside a Vue component. 
>
>    ```vue
>    <template>
>      <button @click="count++">{{ count }}</button>
>    </template>
>                      
>    <script>
>    export default {
>      data() {
>          return {
>              count: 0
>          }
>      },
>      mounted() {
>        console.log(this.count) // 0
>      }
>    }
>    </script>
>    ```
>
>    ![image-20231121114940046](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231121114940046.png)
>
> 2. **Composition API**: Introduced in Vue 3, the Composition API is a set of additive, function-based APIs that allow flexible composition of component logic. It's an alternative to the Options API and is particularly useful when dealing with complex components as it improves code organization and reuse.
>
>    ```vue
>    <template>
>      <button @click="increment()">{{ count }}</button>
>    </template>
>                      
>    <script>
>    import { ref } from 'vue'
>                      
>    export default {
>      setup() {
>        const count = ref(0);
>                      
>        function increment() {
>          count.value++;
>        }
>                      
>        return {
>          count,
>          increment
>        }
>      },
>      mounted() {
>        console.log(this.count) // 0
>      }
>    }
>    </script>
>    ```
>
>    ```vue
>    <template>
>      <button @click="increment()">{{ count }}</button>
>    </template>
>                      
>    <script setup>
>    import { ref, onMounted } from 'vue'
>                      
>    const count = ref(0);
>                      
>    const increment = () => {
>      count.value++;
>    }
>                      
>    onMounted(() => {
>      console.log(count.value); // 0
>    });
>    </script>
>    ```
>
>    ![image-20231121114911043](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231121114911043.png)

## Vue Essentials

https://vuejs.org/guide/introduction.html

### Template Syntax

#### Text Interpolation

> The most basic form of data binding is text interpolation using the "Mustache" syntax (double curly braces):
> `{{` msg`}}`

```vue
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <span>{{ notification }}</span>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      notification: 'Here is a notification!'
    }
  },
  props: {
    msg: String
  }
}
</script>
```

#### Using JavaScript Expressions

> In Vue templates, JavaScript expressions can be used in the following positions:
>
> - Inside **text interpolations** (mustaches)
> - In the **attribute value of any Vue directives** (special attributes that start with `v-`)

```vue
<template>
  <div class="hello">
    <br>
    {{ number + 1 }}
    <br>
    {{ ok ? 'YES' : 'NO' }}
    <br>
    {{ message.split('').reverse().join('') }}
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      number: 10,
      ok: true,
      message: 'Hello Vue!'
    }
  },
}
</script>
```

```vue
<template>
  <div @click="changeId" v-show="id <= 2">Id：{{ id }}</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      id: 1
    }
  },
  methods: {
    changeId() {
      this.id = this.id + 1
    }
  },
}
```

#### Calling Functions

> To call a component-exposed method inside a binding expression:

```vue
<time :title="toTitleDate(date)" :datetime="date">
  {{ formatDate(date) }}
</time>
```

#### Row HTML

> The double mustaches interpret the data as plain text, not HTML. In order to output real HTML, you will need to use the `v-html` directive
>
> ![image-20231121111851999](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231121111851999.png)

```vue
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <span>rowHTML:{{ rowHTML }}</span>
    <br>
    <span v-html="rowHTML"></span>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      rowHTML: '<span style="color: red">This should be red.</span>'
    }
  },
  props: {
    msg: String
  }
}
</script>
```



#### Directives(Built-ins)

> A directive's job is to reactively apply updates to the DOM when the value of its expression changes.
>
> Directives are special attributes with the `v-` prefix.

![image-20231122172050262](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231122172050262.png)

##### v-text

> Update the element's text content.
>
> - **Expects:** `string`
>
> - **Example**
>
>   ```vue
>   <span v-text="msg"></span>
>   <!-- same as -->
>   <span>{{msg}}</span>
>   ```
>
>   

##### v-html

> Update the element's
>
> - **Expects:** `string`
>
> - **Details**
>
>   Contents of `v-html` are inserted as plain HTML - Vue template syntax will not be processed. If you find yourself trying to compose templates using `v-html`, try to rethink the solution by using components instead.
>
> - **Example**
>   ![image-20231121111851999](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231121111851999.png)
>
>   ```vue
>   <template>
>     <div class="hello">
>       <h1>{{ msg }}</h1>
>     </div>
>     <div>
>       <span>rowHTML:{{ rowHTML }}</span>
>       <br>
>       <span v-html="rowHTML"></span>
>     </div>
>   </template>
>           
>   <script>
>   export default {
>     name: 'HelloWorld',
>     data() {
>       return {
>         rowHTML: '<span style="color: red">This should be red.</span>'
>       }
>     },
>     props: {
>       msg: String
>     }
>   }
>   </script>
>   ```
>   
>   

##### v-show

> Toggle the element's visibility based on the truthy-ness of the expression value.
>
> - **Expects:** `any`
>
> - **Details**
>
>   `v-show` works by setting the `display` CSS property via inline styles, and will try to respect the initial `display` value when the element is visible. It also triggers transitions when its condition changes.

##### v-if

> Conditionally render an element or a template fragment based on the truthy-ness of the expression value.
>
> - **Expects:** `any`
>
> - **Details**
>
>   When a `v-if` element is toggled, the element and its contained directives /  components are destroyed and re-constructed. If the initial condition is falsy, then the inner content won't be rendered at all.
>
>   Can be used on `<template>` to denote a conditional block containing only text or multiple elements.
>
>   This directive triggers transitions when its condition changes.
>
>   When used together, `v-if` has a higher priority than `v-for`. We don't recommend using these two directives together on one element
>
> Denote the "else block" for `v-if` or a `v-if` / `v-else-if` chain.
>
> - **Does not expect expression**
>
> - **Details**
>
>   - Restriction: previous sibling element must have `v-if` or `v-else-if`.
>   - Can be used on `<template>` to denote a conditional block containing only text or multiple elements.
>
> - **Example**
>
>   ```vue
>   <div v-if="Math.random() > 0.5">
>     Now you see me
>   </div>
>   <div v-else>
>     Now you don't
>   </div>
>   ```

##### v-else-if 

> Denote the "else if block" for `v-if`. Can be chained.
>
> - **Expects:** `any`
>
> - **Details**
>
>   - Restriction: previous sibling element must have `v-if` or `v-else-if`.
>   - Can be used on `<template>` to denote a conditional block containing only text or multiple elements.
>
> - **Example**
>
>   ```vue
>   <div v-if="type === 'A'">
>     A
>   </div>
>   <div v-else-if="type === 'B'">
>     B
>   </div>
>   <div v-else-if="type === 'C'">
>     C
>   </div>
>   <div v-else>
>     Not A/B/C
>   </div>
>   ```

##### v-for

> Render the element or template block multiple times based on the source data.
> `v-for` can also work on values that implement the Iterable Protocol, including native `Map` and `Set`.
>
> - **Expects:** `Array | Object | number | string | Iterable`
>
> - **Details**
>
>   The directive's value must use the special syntax `alias in expression` to provide an alias for the current element being iterated on:
>
> - Example
>
>   ```vue
>   <div v-for="item in items">
>     {{ item.text }}
>   </div>
>   ```
>
>   Alternatively, you can also specify an alias for the index (or the key if used on an Object):
>
>   ```vue
>   <div v-for="(item, index) in items"></div>
>   <div v-for="(value, key) in object"></div>
>   <div v-for="(value, name, index) in object"></div>
>   ```
>
>   The default behavior of `v-for` will try to patch the elements in-place without moving them. To force  it to reorder elements, you should provide an ordering hint with the `key` special attribute:
>
>   ```vue
>   <div v-for="item in items" :key="item.id">
>     {{ item.text }}
>   </div>
>   ```

##### v-on

> Attach an event listener to the element.
>
> - **Shorthand:** `@`
>
> - **Expects:** `Function | Inline Statement | Object (without argument)`
>
> - **Argument:** `event` (optional if using Object syntax)
>
> - **Modifiers**
>
>   - `.stop` - call `event.stopPropagation()`.
>   - `.prevent` - call `event.preventDefault()`.
>   - `.capture` - add event listener in capture mode.
>   - `.self` - only trigger handler if event was dispatched from this element.
>   - `.{keyAlias}` - only trigger handler on certain keys.
>   - `.once` - trigger handler at most once.
>   - `.left` - only trigger handler for left button mouse events.
>   - `.right` - only trigger handler for right button mouse events.
>   - `.middle` - only trigger handler for middle button mouse events.
>   - `.passive` - attaches a DOM event with `{ passive: true }`.
>
> - **Details**
>
>   The event type is denoted by the argument. The expression can be a method  name, an inline statement, or omitted if there are modifiers present.
>
>   When used on a normal element, it listens to **native DOM events** only. When used on a custom element component, it listens to **custom events** emitted on that child component.
>
>   When listening to native DOM events, the method receives the native event as the only argument. If using inline statement, the statement has access  to the special `$event` property: `v-on:click="handle('ok', $event)"`.
>
>   `v-on` also supports binding to an object of event / listener pairs without an argument. Note when using the object syntax, it does not support any  modifiers.
>
> - **Example**
>
>   ```vue
>   <!-- method handler -->
>   <button v-on:click="doThis"></button>
>             
>   <!-- dynamic event -->
>   <button v-on:[event]="doThis"></button>
>             
>   <!-- inline statement -->
>   <button v-on:click="doThat('hello', $event)"></button>
>             
>   <!-- shorthand -->
>   <button @click="doThis"></button>
>             
>   <!-- shorthand dynamic event -->
>   <button @[event]="doThis"></button>
>             
>   <!-- stop propagation -->
>   <button @click.stop="doThis"></button>
>             
>   <!-- prevent default -->
>   <button @click.prevent="doThis"></button>
>             
>   <!-- prevent default without expression -->
>   <form @submit.prevent></form>
>             
>   <!-- chain modifiers -->
>   <button @click.stop.prevent="doThis"></button>
>             
>   <!-- key modifier using keyAlias -->
>   <input @keyup.enter="onEnter" />
>             
>   <!-- the click event will be triggered at most once -->
>   <button v-on:click.once="doThis"></button>
>             
>   <!-- object syntax -->
>   <button v-on="{ mousedown: doThis, mouseup: doThat }"></button>
>   ```

##### v-bind

> Dynamically bind one or more attributes, or a component prop to an expression.
>
> - **Shorthand:** `:` or `.` (when using `.prop` modifier)
>
> - **Expects:** `any (with argument) | Object (without argument)`
>
> - **Argument:** `attrOrProp (optional)`
>
> - **Modifiers**
>
>   - `.camel` - transform the kebab-case attribute name into camelCase.
>   - `.prop` - force a binding to be set as a DOM property. 3.2+
>   - `.attr` - force a binding to be set as a DOM attribute. 3.2+
>
> - **Usage**
>
>   When used to bind the `class` or `style` attribute, `v-bind` supports additional value types such as Array or Objects. See linked guide section below for more details.
>
>   When setting a binding on an element, Vue by default checks whether the element has the key defined as a property using an `in` operator check. If the property is defined, Vue will set the value as a DOM property instead of an attribute. This should work in most cases,  but you can override this behavior by explicitly using `.prop` or `.attr` modifiers. This is sometimes necessary, especially when [working with custom elements](https://vuejs.org/guide/extras/web-components.html#passing-dom-properties).
>
>   When used for component prop binding, the prop must be properly declared in the child component.
>
>   When used without an argument, can be used to bind an object containing attribute name-value pairs.
>
> - **Example**
>
>   ```vue
>   <!-- bind an attribute -->
>   <img v-bind:src="imageSrc" />
>             
>   <!-- dynamic attribute name -->
>   <button v-bind:[key]="value"></button>
>             
>   <!-- shorthand -->
>   <img :src="imageSrc" />
>             
>   <!-- shorthand dynamic attribute name -->
>   <button :[key]="value"></button>
>             
>   <!-- with inline string concatenation -->
>   <img :src="'/path/to/images/' + fileName" />
>             
>   <!-- class binding -->
>   <div :class="{ red: isRed }"></div>
>   <div :class="[classA, classB]"></div>
>   <div :class="[classA, { classB: isB, classC: isC }]"></div>
>             
>   <!-- style binding -->
>   <div :style="{ fontSize: size + 'px' }"></div>
>   <div :style="[styleObjectA, styleObjectB]"></div>
>             
>   <!-- binding an object of attributes -->
>   <div v-bind="{ id: someProp, 'other-attr': otherProp }"></div>
>             
>   <!-- prop binding. "prop" must be declared in the child component. -->
>   <MyComponent :prop="someThing" />
>             
>   <!-- pass down parent props in common with a child component -->
>   <MyComponent v-bind="$props" />
>             
>   <!-- XLink -->
>   <svg><a :xlink:special="foo"></a></svg>
>   ```
>
>   The `.prop` modifier also has a dedicated shorthand, `.`:
>
>   ```vue
>   <div :someProperty.prop="someObject"></div>
>             
>   <!-- equivalent to -->
>   <div .someProperty="someObject"></div>
>   ```
>
>   The `.camel` modifier allows camelizing a `v-bind` attribute name when using in-DOM templates, e.g. the SVG `viewBox` attribute:
>
>   ```vue
>   <svg :view-box.camel="viewBox"></svg>
>   ```
>
>   `.camel` is not needed if you are using string templates, or pre-compiling the template with a build step.

##### v-model

> Create a two-way binding on a form input element or a component.
>
> - **Expects:** varies based on value of form inputs element or output of components
> - **Limited to:**
>   - `<input>`
>   - `<select>`
>   - `<textarea>`
>   - components
> - **Modifiers**
>   - `.lazy` - listen to `change` events instead of `input`
>   - `.number`- cast valid input string to numbers
>   - `.trim` - trim input

##### v-slot

> Denote named slots or scoped slots that expect to receive props.
>
> - **Shorthand:** `#`
>
> - **Expects:** JavaScript expression that is valid in a function argument position,  including support for destructuring. Optional - only needed if expecting props to be passed to the slot.
>
> - **Argument:** slot name (optional, defaults to `default`)
>
> - **Limited to:**
>
>   - `<template>`
>   - **components** (for a lone default slot with props)
>
> - **Example**
>
>   ```vue
>   <!-- Named slots -->
>   <BaseLayout>
>     <template v-slot:header>
>       Header content
>     </template>
>         
>     <template v-slot:default>
>       Default slot content
>     </template>
>         
>     <template v-slot:footer>
>       Footer content
>     </template>
>   </BaseLayout>
>         
>   <!-- Named slot that receives props -->
>   <InfiniteScroll>
>     <template v-slot:item="slotProps">
>       <div class="item">
>         {{ slotProps.item.text }}
>       </div>
>     </template>
>   </InfiniteScroll>
>         
>   <!-- Default slot that receive props, with destructuring -->
>   <Mouse v-slot="{ x, y }">
>     Mouse position: {{ x }}, {{ y }}
>   </Mouse>
>   ```

##### v-pre

> Skip compilation for this element and all its children.
>
> - **Does not expect expression**
>
> - **Details**
>
>   Inside the element with `v-pre`, all Vue template syntax will be preserved and rendered as-is. The most  common use case of this is displaying raw mustache tags.
>
> - **Example**
>
>   ```vue
>   <span v-pre>{{ this will not be compiled }}</span>
>   ```
>
>   

##### v-once

> Render the element and component once only, and skip future updates.
>
> - **Does not expect expression**
>
> - **Details**
>
>   On subsequent re-renders, the element/component and all its children will  be treated as static content and skipped. This can be used to optimize  update performance.
>
> - **Example**
>
>   ```vue
>   <!-- single element -->
>   <span v-once>This will never change: {{msg}}</span>
>   <!-- the element have children -->
>   <div v-once>
>     <h1>comment</h1>
>     <p>{{msg}}</p>
>   </div>
>   <!-- component -->
>   <MyComponent v-once :comment="msg"></MyComponent>
>   <!-- `v-for` directive -->
>   <ul>
>     <li v-for="i in list" v-once>{{i}}</li>
>   </ul>
>   ```

##### v-memo(3.2+)

> - **Expects:** `any[]`
>
> - **Details**
>
>   Memoize a sub-tree of the template. Can be used on both elements and  components. The directive expects a fixed-length array of dependency  values to compare for the memoization. If every value in the array was  the same as last render, then updates for the entire sub-tree will be  skipped. 
>
>   `v-memo` can also be used on components to manually prevent unwanted updates in  certain edge cases where the child component update check has been  de-optimized. But again, it is the developer's responsibility to specify correct dependency arrays to avoid skipping necessary updates.
>
>   For example:
>
> - **Example**
>
>   ```vue
>   <div v-memo="[valueA, valueB]">
>     ...
>   </div>
>   ```
>
>   When the component re-renders, if both `valueA` and `valueB` remain the same, all updates for this `<div>` and its children will be skipped. In fact, even the Virtual DOM VNode  creation will also be skipped since the memoized copy of the sub-tree  can be reused.
>
>   It is important to specify the memoization array correctly, otherwise we may skip updates that should indeed be applied. `v-memo` with an empty dependency array (`v-memo="[]"`) would be functionally equivalent to `v-once`.
>
>   **Usage with `v-for`**
>
>   `v-memo` is provided solely for micro optimizations in performance-critical  scenarios and should be rarely needed. The most common case where this  may prove helpful is when rendering large `v-for` lists (where `length > 1000`):
>
>   ```vue
>   <div v-for="item in list" :key="item.id" v-memo="[item.id === selected]">
>     <p>ID: {{ item.id }} - selected: {{ item.id === selected }}</p>
>     <p>...more child nodes</p>
>   </div>
>   ```
>
>   When the component's `selected` state changes, a large amount of VNodes will be created even though most of the items remained exactly the same. The `v-memo` usage here is essentially saying "only update this item if it went from non-selected to selected, or the other way around". This allows every  unaffected item to reuse its previous VNode and skip diffing entirely.  Note we don't need to include `item.id` in the memo dependency array here since Vue automatically infers it from the item's `:key`.

##### v-cloak

> Used to hide un-compiled template until it is ready.
>
> - **Does not expect expression**
>
> - **Details**
>
>   **This directive is only needed in no-build-step setups.**
>
>   When using in-DOM templates, there can be a "flash of un-compiled  templates": the user may see raw mustache tags until the mounted  component replaces them with rendered content.
>
>   `v-cloak` will remain on the element until the associated component instance is mounted. Combined with CSS rules such as `[v-cloak] { display: none }`, it can be used to hide the raw templates until the component is ready.
>
> - **Example**
>
>   ```vue
>   <template>
>       <div v-cloak>
>         {{ message }}
>       </div>
>   </template>
>             
>   <style>
>       [v-cloak] {
>         display: none;
>       }
>   </style>
>   ```
>
>   The `<div>` will not be visible until the compilation is done.



#### Custom Directives

> Vue.js also allows you to define your own custom directives. This can be useful when you want to create reusable code that manipulates the DOM
>
> ```vue
> <!-- AnyComponent.vue -->
> <template>
>   <input v-focus>
> </template>
> ```
>
> ```javascript
> // main.js
> import { createApp } from 'vue'
> import App from './App.vue'
> import router from './router'
> import store from './store'
> 
> const app = createApp(App)
> 
> //Registers a global custom directive
> app.directive('focus', {
>   mounted(el) {
>     el.focus()
>   }
> })
> 
> // register (function directive shorthand)
> app.directive('my-directive', () => {
>   // this will be called for both `mounted` and `updated`
> })
> 
> // register (object directive)
> app.directive('my-directive', {
>   /* custom directive hooks */
>   created(el, binding, vnode, prevVnode) {
>       //el: the element the directive is bound to. This can be used to directly manipulate the DOM.
>       //binding: an object containing the following properties.
>       //vnode: the underlying VNode representing the bound element.
>       //prevNode: the VNode representing the bound element from the previous render. Only available in the beforeUpdate 		and updated hooks.
>   },
>   beforeMount(el, binding, vnode, prevVnode) {},
>   mounted(el, binding, vnode, prevVnode) {},
>   beforeUpdate(el, binding, vnode, prevVnode) {},
>   updated(el, binding, vnode, prevVnode) {},
> })
> 
> // retrieve a registered directive
> const myDirective = app.directive('my-directive')
> 
> app.use(store).use(router).mount('#app')
> ```
>
> 

### Reactivity

#### Reactive Properties(Data) & Methods

```vue
<!-- Options API -->
<template>
  <button @click="increment">
    {{ count }}
  </button>
</template>

<script>
    export default {
      data() {
        return {
          count: 0
        }
      },
      methods: {
        increment() {
          this.count++
        }
      },
    }
</script>
```

```vue
<!-- Composition API -->
<template>
  <button @click="increment">
    {{ count }}
  </button>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}
</script>

```

#### Computed Properties

> **computed properties are `cached` based on their reactive dependencies.** 
> A computed property will only re-evaluate when some of its reactive dependencies have changed. 
>
> Computed properties are by **default getter-only**. If you attempt to **assign a new value to a computed property**, you will **receive a runtime warning**.
>
> - **Getter-only Computed**
> - **Writable Computed**

```vue
<!-- Options API -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span>
    <p>FullName:</p>
    <span>{{ fullName }}</span>
  </div>
  <div>
    <button @click="changeFullName">Click me to change fullName</button>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
      author: {
        firstName: 'Eddie',
        lastName: 'Zhang',
        books: [
          'Vue 2 - Advanced Guide',
          'Vue 3 - Basic Guide',
          'Vue 4 - The Mystery'
        ]
      }
    }
  },
  methods: {
    changeFullName() {
      this.fullName = 'Eddie ZhangTurbo'
    }
  },
  computed: {
    // Computed properties are by default getter-only.
    publishedBooksMessage() {
      // `this` points to the component instance
      return this.author.books.length > 0 ? 'Yes' : 'No'
    },
    //Writable Computed
    fullName: {
      // getter
      get() {
        return this.author.firstName + ' ' + this.author.lastName
      },
      // setter
      set(newValue) {
        // Note: we are using destructuring assignment syntax here.
        [this.author.firstName, this.author.lastName] = newValue.split(' ')
      }
    }
  },
  props: {
    msg: String
  }
}
</script>
```

```vue
<!-- Composition API -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span>
    <p>FullName:</p>
    <span>{{ fullName }}</span>
  </div>
  <div>
    <button @click="changeFullName">Click me to change fullName</button>
  </div>
</template>

<script setup>
import { ref, computed, defineProps } from 'vue'

const author = ref({
  firstName: 'Eddie',
  lastName: 'Zhang',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

const changeFullName = () => {
  fullName.value = 'Eddie ZhangTurbo'
}

const publishedBooksMessage = computed(() => {
  // Computed properties are by default getter-only.
  return author.value.books.length > 0 ? 'Yes' : 'No'
})

const fullName = computed({
  // getter
  get() {
    return author.value.firstName + ' ' + author.value.lastName
  },
  // setter
  set(newValue) {
    // Note: we are using destructuring assignment syntax here.
    [author.value.firstName, author.value.lastName] = newValue.split(' ')
  }
})

defineProps({
  msg: String
})

</script>
```



#### Watchers

> ### **Several types of Watchers**
>
> `watch` is **shallow** & **lazy** by default
>
> - **Shallow Watchers (Default)**
>
>   The callback will **only trigger when the watched property has been assigned a new value** - it **won't  trigger on nested property changes.**
>
> - **Deep Watchers**
>
>   Trigger on all nested property changes.
>
>   `deep: true`
>
> - **Eager Watchers**
>   This is useful when you want to **perform an action** right away based on the **initial state of your data**.
>
>   Force a watcher's **callback to be executed immediately(before the component is `mounted`)** 
>
>   `immediate: true`
>
> 
>
> ### **watchEffect()**
>
> - `watch` only **tracks the explicitly watched source**. It won't  track anything accessed inside the callback. In addition, the callback  **only triggers when the source has actually changed**. watch separates dependency tracking from the side effect, giving us more precise control over when the callback should fire.
>
>   ```javascript
>   <script setup>
>   import { ref, watch } from 'vue';
>   
>   let question = ref({ question: '' });
>   
>   //need to specify the source or sources to watch as the first argument
>   watch(() => question.value.question, newQuestion => {
>     question.value.question = 'Will I be a billionare?'
>   }, { immediate: true });
>   
>   <script/>
>   ```
>
> - `watchEffect`, It automatically **tracks every reactive property accessed during its synchronous execution**. This is  more convenient and typically results in terser code, but makes its  reactive dependencies less explicit.
>
>   ```javascript
>   <script setup>
>   import { ref, watchEffect } from 'vue';
>               
>   let question = ref({ question: '' });
>   let answer = ref('Questions usually contain a question mark.');
>   let loading = ref(false);
>               
>   //tracks all reactive dependencies within the provided function
>   watchEffect(
>     () => {
>       console.log("question.value.question:",question.value.question);
>       console.log("answer:",answer.value);
>       console.log("loading:",loading.value);
>     }
>   );
>               
>   <script/>
>   ```
>
>   
>
> ### **Stopping a Watcher**
>
> Watchers declared using the `watch` option or the `$watch()` instance method | declared synchronously inside `setup()` or `<script setup>` are bound to the owner component instance, and will be **automatically  stopped** when the **owner component is unmounted**. In most cases, you don't  need to worry about stopping the watcher yourself.
>
> **To manually stop a watcher**, use the returned handle function. This works for both `watch` and `watchEffect`:
>
> ```javascript
> const unwatch = watchEffect(() => {})
> 
> // ...later, when no longer needed
> unwatch()
> ```
>
> 
>
> ### **Callback Flush Timing**
>
> **By default,** user-created watcher callbacks are called **before** Vue component **updates**. 
>
> If you want to access the DOM in a watcher callback **after** Vue has **updated** it, you need to specify the `flush: 'post'` option:
>
> ```javascript
> import { watchPostEffect } from 'vue'
> 
> //Post-flush watchEffect() also has a convenience alias, watchPostEffect():
> watchPostEffect(() => {
>   /* executed after Vue updates */
> })
> 
> watch(source, callback, {
>   flush: 'post'
> })
> 
> watchEffect(callback, {
>   flush: 'post'
> })
> ```
>
> 

##### Shallow Watchers (Default)

```vue
<!-- Options API -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question" :disabled="loading" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: '',
      answer: 'Questions usually contain a question mark.',
      loading: false
    }
  },
  watch: {
    // whenever question changes, this function will run
    question(newQuestion, oldQuestion) {
      console.log(oldQuestion)
      if (newQuestion.includes('?')) {
        this.getAnswer()
      }
    }
  },
  methods: {
    async getAnswer() {
      this.loading = true
      this.answer = 'Thinking...'
      try {
        const res = await fetch('https://yesno.wtf/api')
        console.log(res)
        this.answer = (await res.json()).answer
      } catch (error) {
        this.answer = 'Error! Could not reach the API. ' + error
      } finally {
        this.loading = false
      }
    }
  },
  props: {
    msg: String
  },
}

</script>
```

```vue
<!-- Composition API -->
<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question" :disabled="loading" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';

const question = ref('');
const answer = ref('Questions usually contain a question mark.');
const loading = ref(false);

const getAnswer = async () => {
  loading.value = true;
  answer.value = 'Thinking...';
  try {
    const res = await fetch('https://yesno.wtf/api');
    answer.value = (await res.json()).answer;
  } catch (error) {
    answer.value = 'Error! Could not reach the API. ' + error;
  } finally {
    loading.value = false;
  }
};

watch(question, (newQuestion, oldQuestion) => {
  //whenever question changes, this function will run
  console.log(newQuestion, oldQuestion);
  if (newQuestion.includes('?')) {
    getAnswer();
  }
});
</script>
```

##### Deep Watchers

```vue
<!-- Options API -->
<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question.question" :disabled="loading" style="width: 200px" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: { question: '' },
      answer: 'Questions usually contain a question mark.',
      loading: false,
    };
  },
  watch: {
    'question.question': {
      deep: true,//deep: true will watch for changes in nested objects
      handler(newQuestion) {
        if (newQuestion.includes('?')) {
          this.getAnswer();
        }
      },
    },
  },
  methods: {
    async getAnswer() {
      this.loading = true;
      this.answer = 'Thinking...';
      try {
        const res = await fetch('https://yesno.wtf/api');
        this.answer = (await res.json()).answer;
      } catch (error) {
        this.answer = 'Error! Could not reach the API. ' + error;
      } finally {
        this.loading = false;
      }
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
```

```vue
<!-- Composition API -->
<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question.question" :disabled="loading" style="width: 200px" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';

const question = ref({ question: '' });
const answer = ref('Questions usually contain a question mark.');
const loading = ref(false);

const getAnswer = async () => {
  loading.value = true;
  answer.value = 'Thinking...';
  try {
    const res = await fetch('https://yesno.wtf/api');
    answer.value = (await res.json()).answer;
  } catch (error) {
    answer.value = 'Error! Could not reach the API. ' + error;
  } finally {
    loading.value = false;
  }
};

watch(question, (newQuestion) => {
  if (newQuestion.question.includes('?')) {
    getAnswer();
  }
}, { deep: true });//deep: true will watch for changes in nested objects
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>

```

##### Eager Watchers

```vue
<!-- Options API -->
<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question.question" :disabled="loading" style="width: 200px" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: { question: '' },
      answer: 'Questions usually contain a question mark.',
      loading: false,
    };
  },
  watch: {
    'question.question': {
      immediate: true,//immediate: true means that the watcher will be triggered instantly before the component is mounted.
      handler(newQuestion) {
        this.question.question = 'Will I be a billionare?'
        if(newQuestion.endsWith('?')){
          this.getAnswer();
        }
      },
    },
  },
  methods: {
    async getAnswer() {
      this.loading = true;
      this.answer = 'Thinking...';
      try {
        const res = await fetch('https://yesno.wtf/api');
        this.answer = (await res.json()).answer;
      } catch (error) {
        this.answer = 'Error! Could not reach the API. ' + error;
      } finally {
        this.loading = false;
      }
    },
  },
};
</script>
```

```vue
<!-- Composition API -->
<template>
  <div>
    <p>
      Ask a yes/no question:
      <input v-model="question.question" :disabled="loading" style="width: 200px" />
    </p>
    <p>{{ answer }}</p>
  </div>
</template>

<script setup>
import { ref, watch } from 'vue';

let question = ref({ question: '' });
let answer = ref('Questions usually contain a question mark.');
let loading = ref(false);

watch(() => question.value.question, newQuestion => {
  question.value.question = 'Will I be a billionare?'
  if(newQuestion.endsWith('?')){
    getAnswer();
  }
}, { immediate: true });//immediate: true makes the watcher fire immediately before the component is mounted

async function getAnswer() {
  loading.value = true;
  answer.value = 'Thinking...';
  try {
    const res = await fetch('https://yesno.wtf/api');
    answer.value = (await res.json()).answer;
  } catch (error) {
    answer.value = 'Error! Could not reach the API. ' + error;
  } finally {
    loading.value = false;
  }
}

</script>
```



#### Methods | Computed | Watch

> In Vue.js, `methods`, `computed`, and `watch` are different ways to react to data changes:
>
> 1. `methods`: These are functions that you can call from within your Vue component. They are **not cached** and will **always run whenever they're called**.
> 2. `computed`: These are functions that are used to compute derived data based on your component's data. They are **cached** based on their dependencies, and only **re-evaluate when some of its dependencies have changed**.
> 3. `watch`: This is used to perform asynchronous or expensive operations in response to changing data. When a data property that is being watched changes, the function specified gets executed.

```vue
<!-- Options API -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <p>FullName:</p>
    <span>{{ fullNameComputed }}</span>
  </div>
  <div>
    <button @click="changeName">Click me to changeName</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstName: 'eddie',
      lastName: 'Zhang',
      fullName: '',
    };
  },
  methods: {
    changeName() {
      this.firstName = 'Eddie';
    },
  },
  computed: {
    fullNameComputed() {
      return this.firstName + " " + this.lastName;
    },
  },
  watch: {
    firstName(newVal, oldVal) {
      console.log('firstName changed', newVal, oldVal);
      this.fullName = newVal + " " + this.lastName;
    },
  },
  props: {
    msg: String
  }
};
</script>
```

```vue
<!-- Composition API -->
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
  <div>
    <p>FullName:</p>
    <span>{{ fullName }}</span>
  </div>
  <div>
    <button @click="changeName">Click me to changeName</button>
  </div>
</template>

<script setup>
import { ref, computed, watch } from 'vue';


let msg = ref('Hello World');
let firstName = ref('eddie');
let lastName = ref('Zhang');
let fullName = computed(() => `${firstName.value} ${lastName.value}`);

let changeName = () => {
  firstName.value = 'Eddie';
};

watch(firstName, (newVal, oldVal) => {
  console.log('firstName changed', newVal, oldVal);
});

</script>
```

#### Lifecycle Hooks

[Options Lifecycle Hooks](https://vuejs.org/api/options-lifecycle.html)

```vue
<!-- Options API -->
<template>
  <button @click="increment">
    {{ count }}
  </button>
</template>

<script>
    export default {
      data() {
        return {
          count: 0
        }
      },
      methods: {
        increment() {
          this.count++
        }
      },
      beforeCreate(){},
	  created(){},
	  beforeMount(){},
      mounted() {
        // methods can be called in lifecycle hooks, or other methods!
        this.increment()
      }, 
	  beforeUpdate(){},
      updated(){},
	  beforeUnmount(){},
      unmounted(){},
	  errorCaptured(){},
      renderTracked(){},
      renderTriggered(){},
	  activated(){},
	  deactivated(){},
      serverPrefetch(){},
    }
</script>
```

[Composition Lifecycle Hooks](https://vuejs.org/api/composition-api-lifecycle.html)

```vue
<!-- Composition API -->
<template>
  <button id="count" @click="increment">
    {{ count }}
  </button>
</template>

<script setup>
import { ref,onMounted, onUpdated } from 'vue'

const count = ref(0)

function increment() {
  count.value++
}

onMounted(() => {
  console.log(`the component is now mounted.`)
})
onUpdated(() => {
  // text content should be the same as current `count.value`
  console.log(document.getElementById('count').textContent)
})

</script>
```

#### Template Refs

> `ref` is **used to register a reference to an element or a child component**
>
> `ref` attribute can be **dynamically bound to a function**. (In Vue 3)

##### Accessing the refs

> ```vue
> <template>
>   <div>
>     <input ref="input">
>   </div>
> </template>
> ```
>
> - **Options API**
>
>   `this.$refs`
>
>   ```vue
>   <script>
>   export default {
>     mounted() {
>       //this.$refs
>       this.$refs.input.focus()//this.$refs.input, or you can say this.refs["input"]
>     }
>   }
>   </script>
>   ```
>
> - **Composition API**
>
>   Declare a ref with the same name:
>
>   ```vue
>   <script setup>
>   import { ref, onMounted } from 'vue'
>               
>   // declare a ref to hold the element reference
>   // the name must match template ref value
>   const input = ref(null)
>               
>   onMounted(() => {
>     input.value.focus()
>   })
>   </script>
>   ```
>
>   

##### Ref DOM Element

> Vue’s `ref` helps you **“reference” DOM elements in a more efficient way**.  The use of JavaScript’s `getElementById` **is not encouraged** in Vue.
>
> Note that you can only access the ref **after the component is mounted.**

```vue
<!-- Options API -->
<template>
  <div>
    <input ref="input">
  </div>
</template>

<script>
export default {
  mounted() {
    //this.$refs
    this.$refs.input.focus()//this.$refs.input, or you can say this.refs["input"]
  }
}
</script>
```

```vue
<!-- Composition API -->
<template>
  <div>
    <input ref="input">
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// declare a ref to hold the element reference
// the name must match template ref value
const input = ref(null)

onMounted(() => {
  input.value.focus()
})
</script>
```

##### Refs inside v-for

> When `ref` is used inside `v-for`, the resulting ref value will be an array containing the corresponding elements

![image-20231122104243070](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231122104243070.png)

```vue
<!-- Options API -->
<template>
  <div>
    <ul>
      <li v-for="item in list" :key="item" ref="item">{{ item }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [1, 2, 3]
    };
  },
  mounted() {
    console.log("item:", this.$refs.item);
  }
</script>
```

```vue
<!-- Composition API -->
<template>
  <div>
    <ul>
      <li v-for="item in list" :key="item" ref="item">{{ item }}</li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';

let list = ref([1, 2, 3]);

const item = ref(null);

onMounted(() => {
  console.log("item:",item.value);
});
</script>
```

##### Function Refs

> In Vue 3, the `ref` attribute can be dynamically **bound to a function.** 
> **This function will be called when the component is mounted** and **the argument will be the actual DOM element.** 
> When the **component is unmounted, the argument will be null.**

![image-20231122144717809](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231122144717809.png)

```vue
<!-- Options API -->
<template>
  <div>
    //This function will be called when the component is mounted and el will be the actual DOM element.
    <input :ref="(el) => { console.log(el) }" type="text">
    <input :ref="setInputRef" type="text">
    <button @click="focusInput">Focus the input</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      inputElement: null
    };
  },
  methods: {
    setInputRef(el) {
      if (el) {
        // The component is mounted and el is the actual DOM element
        el.value = `Here is Function Refs`;
        this.inputElement = el;
      }
    },
    focusInput() {
      this.inputElement.focus();
    }
    }
  }
}
</script>
```

```vue
<!-- Composition API -->
<template>
  <div>
    //This function will be called when the component is mounted and el will be the actual DOM element.
    <input :ref="(el) => { console.log(el) }" type="text">
    <input :ref="setInputRef" type="text">
    <button @click="focusInput">Focus the input</button>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const inputElement = ref(null);

const setInputRef = (el) => {
  if (el) {
    // The component is mounted and el is the actual DOM element
    el.value = `Here is Function Refs`;
    inputElement.value = el;
  } else {
    // The component is unmounted and el is null
    // Perform cleanup if necessary
    inputElement.value = null;
  }
}
const focusInput = () => {
  inputElement.value.focus();
}

</script>
```

##### Ref on Component

> `ref` can also be used **on a child component**. the **reference** will be that of a **component instance**:
>
> `ref` is used for more direct manipulation or access to a DOM element or child component, and should be avoided if possible.
>
> In most cases, you should **try to implement parent / child interactions using the standard props and emit interfaces first.** so component refs should be only used when absolutely needed 

When using **Options API**: This allows to directly access the child component's properties and methods.
The `expose` option can **be used to limit the access to a child instance:**

```vue
<!-- Options API -->
<template>
  <Child ref="child" />
</template>

<script>
import Child from './Child.vue'

export default {
  components: {
    Child
  },
  mounted() {
    // this.$refs.child will hold an instance of <Child />
    console.log(this.$refs.child); // Logs the Child component instance
  }
}
</script>

<!-- Options API -->
<script>
    export default {
      expose: ['publicData', 'publicMethod'],
      data() {
        return {
          publicData: 'foo',
          privateData: 'bar'
        }
      },
      methods: {
        publicMethod() {
          /* ... */
        },
        privateMethod() {
          /* ... */
        }
      }
    }
</script>
```

When using Composition API `<script setup>` are **private by default**:

Child component chooses to **expose a public interface using** the `defineExpose` macro:

```vue
<!-- Composition API -->
<template>
  <Child ref="child" />
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Child from './Child.vue'

const child = ref(null)

onMounted(() => {
  // child.value will hold an instance of <Child />
  console.log(child.value);// Logs the Child component instance
})
</script>

<!-- Composition API -->
<script setup>//are private by default
import { ref } from 'vue'

const a = 1
const b = ref(2)

// Compiler macros, such as defineExpose, don't need to be imported
defineExpose({
  a,
  b
})
</script>
```

#### Conditional Rendering 

#### List Rendering

#### Event Handling

#### Form Input Bindings

### Application instance

> Every app requires a **"root component"** that can contain other components as its children.
>
> ![image-20231123114122778](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231123114122778.png)
>
> ### 3.x
>
> Every Vue application starts by creating a new **application instance** with the `createApp`
>
> ```javascript
> <!-- Main.js -->
> import { createApp } from 'vue'
> import App from './App.vue'// import the root component App from a single-file component.
> 
> const app = createApp(App)
> ```
>
> ### 2.x
>
> A Vue application consists of a **root Vue instance** created with `new Vue`
>
> ```javascript
> <!-- Main.js -->
> import Vue from 'vue'
> import App from './App.vue'// import the root component App from a single-file component.
> 
> new Vue({
>     render: h => h(App)
> }).$mount('#app')
> ```
>
> 

### Application API

> #### Application API 3.x
>
> #### Global API
>
> - [createApp()](https://vuejs.org/api/application.html#createapp)
> - [createSSRApp()](https://vuejs.org/api/application.html#createssrapp)
> - [app.mount()](https://vuejs.org/api/application.html#app-mount)
> - [app.unmount()](https://vuejs.org/api/application.html#app-unmount)
> - [app.component()](https://vuejs.org/api/application.html#app-component)
> - [app.directive()](https://vuejs.org/api/application.html#app-directive)
> - [app.use()](https://vuejs.org/api/application.html#app-use)
> - [app.mixin()](https://vuejs.org/api/application.html#app-mixin)
> - [app.provide()](https://vuejs.org/api/application.html#app-provide)
> - [app.runWithContext()](https://vuejs.org/api/application.html#app-runwithcontext)
> - [app.version](https://vuejs.org/api/application.html#app-version)
>
> #### Global Config
>
> - [app.config](https://vuejs.org/api/application.html#app-config)
> - [app.config.errorHandler](https://vuejs.org/api/application.html#app-config-errorhandler)
> - [app.config.warnHandler](https://vuejs.org/api/application.html#app-config-warnhandler)
> - [app.config.performance](https://vuejs.org/api/application.html#app-config-performance)
> - [app.config.compilerOptions](https://vuejs.org/api/application.html#app-config-compileroptions)
> - [app.config.globalProperties](https://vuejs.org/api/application.html#app-config-globalproperties)
> - [app.config.optionMergeStrategies](https://vuejs.org/api/application.html#app-config-optionmergestrategies)

> #### Application API 2.x
>
> #### Global Config
>
> - [silent](https://v2.vuejs.org/v2/api/#silent)
> - [optionMergeStrategies](https://v2.vuejs.org/v2/api/#optionMergeStrategies)
> - [devtools](https://v2.vuejs.org/v2/api/#devtools)
> - [errorHandler](https://v2.vuejs.org/v2/api/#errorHandler)
> - [warnHandler](https://v2.vuejs.org/v2/api/#warnHandler)
> - [ignoredElements](https://v2.vuejs.org/v2/api/#ignoredElements)
> - [keyCodes](https://v2.vuejs.org/v2/api/#keyCodes)
> - [performance](https://v2.vuejs.org/v2/api/#performance)
> - [productionTip](https://v2.vuejs.org/v2/api/#productionTip)
>
> #### Global API
>
> - [Vue.extend](https://v2.vuejs.org/v2/api/#Vue-extend)
> - [Vue.nextTick](https://v2.vuejs.org/v2/api/#Vue-nextTick)
> - [Vue.set](https://v2.vuejs.org/v2/api/#Vue-set)
> - [Vue.delete](https://v2.vuejs.org/v2/api/#Vue-delete)
> - [Vue.directive](https://v2.vuejs.org/v2/api/#Vue-directive)
> - [Vue.filter](https://v2.vuejs.org/v2/api/#Vue-filter)
> - [Vue.component](https://v2.vuejs.org/v2/api/#Vue-component)
> - [Vue.use](https://v2.vuejs.org/v2/api/#Vue-use)
> - [Vue.mixin](https://v2.vuejs.org/v2/api/#Vue-mixin)
> - [Vue.compile](https://v2.vuejs.org/v2/api/#Vue-compile)
> - [Vue.observable](https://v2.vuejs.org/v2/api/#Vue-observable)
> - [Vue.version](https://v2.vuejs.org/v2/api/#Vue-version)

### Vue Components

> **A Vue component is a reusable Vue instance** with a name. 
>
> Using **PascalCase names** when registering components
>
> It's like a custom element that you can use in other parts of your application. Components are one of the most powerful features of Vue.js, allowing you to build reusable pieces of your application's interface.
>
> - Components in Vue.js have their own state, markup, and logic encapsulated in them. 
> - They can have props for passing data from parent to child.
> - Emit custom events for parent-child communication.
> - Use slots for content distribution.
> - Have their own lifecycle hooks.
> - ...etc.

![image-20230329172014909](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329172014909.png)

> 1.一个重要的内置关系：VueComponent.prototype.__proto__ === Vue.prototype
>
> 2.为什么要有这个关系：让组件实例对象（VueComponent）可以访问到 Vue原型上的属性、方法。相当于和vm实例对象一样的功能

![image-20230329191208971](C:/Users/ZJH20/AppData/Roaming/Typora/typora-user-images/image-20230329191208971.png)

#### Define & Use

> Typically define each Vue component in a dedicated file using the `.vue` extension

##### Define a Component

```vue
<!-- Options API -->
<template>
  <button @click="count++">You clicked me {{ count }} times.</button>
</template>

<script>
export default {
  name: 'EddieComponent',
  //It's not mandatory to provide a name option for a Vue component,It helps in debugging. 
  //When you don't provide a name option, Vue will infer a name based on its location in the module system. 
  //But, if you provide a name option, it will be used as the component's name in the debugger.
  data() {
    return {
      count: 0
    }
  }
}
</script>
```

```vue
<!-- Composition API -->
<template>
  <button @click="count++">You clicked me {{ count }} times.</button>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>
```

##### Use Component

> To use a child component. 
>
> - we need to `import` it in the parent component. 
>
> - we need to **register** it with the `components` option. 

```vue
<!-- Options API -->
<template>
  <h1>Here is a child component!</h1>
  <ButtonCounter />
</template>

<script>
import ButtonCounter from './ButtonCounter.vue'

export default {
  components: {
    ButtonCounter
  }
}
</script>
```

```vue
<!-- Composition API -->
<template>
  <h1>Here is a child component!</h1>
  <ButtonCounter />
</template>

<script setup>
import ButtonCounter from './ButtonCounter.vue'
</script>
```



#### Registration

> A Vue component needs to be "registered" so that Vue knows where to  locate its implementation when it is encountered in a template. 
> There  are two ways to register components: global and local.

##### Local Registration

> Local registration scopes the availability of the registered components to the current component only. 
>
> Local registration is done using the `components` option:
>
> When using SFC with `<script setup>`, imported components can be locally used without registration:

```vue
<!-- Options API -->
<template>
  <h1>Here is a child component!</h1>
  <ButtonCounter />
</template>

<script>
import ButtonCounter from './ButtonCounter.vue'

export default {
  components: {
    ButtonCounter
  }
}
</script>
```

```vue
<!-- Composition API -->
<template>
  <h1>Here is a child component!</h1>
  <ButtonCounter />
</template>

<script setup>
import ButtonCounter from './ButtonCounter.vue'
</script>
```

##### Global Registration

> We can make components available globally in the current **Vue application(Main.js)** using the `.component()` method:
> The `.component()` method can be chained
>
> 
>
> While convenient, global registration has a few **drawbacks**:
>
> 1. Global registration prevents build systems from removing unused components  (a.k.a "tree-shaking"). If you globally register a component but end up  not using it anywhere in your app, it will still be included in the  final bundle.
> 2. Global registration makes dependency  relationships less explicit in large applications. It makes it difficult to locate a child component's implementation from a parent component  using it. This can affect long-term maintainability similar to using too many global variables.

```javascript
<!-- Main.js -->
import { createApp } from 'vue'

const app = createApp({})

app.component(
  // the registered name
  'MyComponent',
  // the implementation
  {
    /* ... */
  }
)
.component('ComponentA', ComponentA)
.component('ComponentB', ComponentB)
.component('ComponentC', ComponentC)
```

#### Communication

> In Vue, components are used to create reusable code structures. There are several ways for components to communicate in Vue
>
> 1. **Props and Events**: This is the most common way of communication **between parent and child components**. 
>    - The parent passes data to the child via `props`**(Parent --> Child)**
>    - The child communicates back to the parent via `events`**(Child --> Parent)**
>
> 2. **Provide / Inject**: This is a less common way of communication, typically used for dependency injection. 
>
>    Regardless of how deep it is, **Any component in the descendant tree can `inject` dependencies `provided` by components up in its parent chain**.
>
> 3. **Vuex**: Vuex is a state management library for Vue.js. It serves as a centralized store for all the components in an application. Components can read state from the store, and commit mutations to change the state.
>
> 4. **Event Bus**: This is a less common and not recommended way of communication, typically used for communication between sibling components. An empty Vue instance is used as a central event bus, components can emit event to, and listen to events on the event bus.
>
> 5. **Slots**: They can be used to **pass a template fragment**  from a parent component into child components.

##### Props and Events

![image-20231123143655865](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231123143655865.png)

> This is the most common way of communication **between parent and child components**. 

```vue
<!-- Options API -->

// ParentComponent.vue
<template>
  <ChildComponent :message="parentMessage" @childEvent1="handleChildEvent"/>
</template>

<script>
import ChildComponent from './ChildComponent.vue'

export default {
  components: {
    ChildComponent
  },
  data() {
    return {
      parentMessage: 'Hello from parent'
    }
  },
  methods: {
    handleChildEvent(payload) {
      console.log('Received event from child with payload:', payload)
    }
  }
}
</script>


// ChildComponent.vue
<template>
  <button @click="emitEvent">Click me</button>
  //A component can emit custom events directly in template expressions using the built-in $emit method:
  <button @click="$emit('childEvent1', 'Hello from child')">Click me</button>
</template>

<script>
export default {
  //props: ['message'],
  props: {
    message: String
  },
  methods: {
    emitEvent() {
      this.$emit('childEvent2', 'Hello from child')//emit a custom event
    }
  },
  mounted() {
    console.log(this.message) // logs: 'Hello from parent'
  }
}
</script>
```

```vue
<!-- Composition API -->

<!-- ParentComponent.vue -->
<template>
  <ChildComponent :message="parentMessage" @childEvent1="handleChildEvent"/>
</template>

<script setup>
import ChildComponent from './ChildComponent.vue'

const parentMessage = 'Hello from parent'

const handleChildEvent = (payload) => {
  console.log('Received event from child with payload:', payload)
}
</script>


<!-- ChildComponent.vue -->
<template>
  //A component can emit custom events directly in template expressions using the built-in $emit method:
  <button @click="$emit('childEvent1', 'Hello from child')">Click me</button>
  <button @click="submitForm">Click me</button>
</template>

<script setup>
import { ref, onMounted } from 'vue'

//const props = defineProps(['message'])
const props = defineProps({
  message: String
})

const emits = defineEmits({
  // No validation
  click: null,

  // Validate submit event
  submit: ({ email, password }) => {
    if (email && password) {
      return true
    } else {
      console.warn('Invalid submit event payload!')
      return false
    }
  }
})

function submitForm(email, password) {
  emit('submit', { email, password })//emit a custom event
}

onMounted(() => {
  console.log(props.message) // logs: 'Hello from parent'
})
</script>
```



##### Provide / Inject

![image-20231123142618942](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231123142618942.png)

> **A parent component** can serve as a **dependency provider** for all its descendants. 
>
> Any component in the descendant tree, regardless of how deep it is, can inject dependencies provided by components up in its parent chain.
>
> This can be useful for avoiding prop drilling, where you have to pass props through multiple layers of components.

###### App-level Provide

```javascript
<!-- main.js -->
import { createApp } from 'vue'

const app = createApp({})

app.provide(/* key */ 'message', /* value */ 'hello!')
```

###### Component Provide / Inject

```vue
<!-- Options API -->

<!-- provide -->
<script>
    export default {
      data() {
        return {
          message: 'hello!'
        }
      },
      provide() {
        // use function syntax so that we can access `this`
        return {
          message: this.message
        }
      }
    }
</script>
<!-- inject -->
<script>
    export default {
      //inject: ['message'],
      inject: {
        message: {
          from: 'message', // this is optional if using the same key for injection
          default: 'default value'
        },
        user: {
          // use a factory function for non-primitive values that are expensive
          // to create, or ones that should be unique per component instance.
          default: () => ({ name: 'John' })
        }
      },
      data() {
        return {
          // initial data based on injected value
          fullMessage: this.message
        }
      }
    }
</script>
```

```vue
<!-- Composition API -->

<!-- provide -->
<script setup>
    import { ref, provide } from 'vue'

    const message = ref('hello')
    provide('message', message)
</script>
<!-- inject -->
<script setup>
    import { inject } from 'vue'
    
    //const message = inject('message')
    
    // `value` will be "default value"
    // if no data matching "message" was provided
    const value = inject('message', 'default value')
</script>
```

###### Working with Reactivity

##### Vuex

##### Event Bus

##### Slots

![image-20231123153646211](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231123153646211.png)

> They can be used to **pass a template fragment from a parent component into child components**.
>
> - There are two types of slots in Vue: **default slots** and **named slots**.
>
> - Specify **fallback (default)  content** for a slot, to be rendered only when the parent didn't provide any slot content. 
>
> - **Scoped slots** are a feature in Vue.js that allow you to access child component data in the parent component.
>
>   Slot content has access to the data scope of the parent component, because it is defined in the parent.
>
>   Slot content does not have access to the child component's data.

###### **Default slots**

> Allow you to pass any number of elements from the parent component to the child component. These elements will replace the content inside the `<slot></slot>` tags in the child component.

```vue
<!-- ChildComponent.vue -->
<template>
  <div>
    <slot></slot>
  </div>
</template>

<!-- ParentComponent.vue -->
<template>
  <ChildComponent>
    <p>This is some content passed from the parent.</p>
  </ChildComponent>
</template>
```

###### **Named slots**

> Allow you to define multiple slots and decide where to place the content in the child component. You can name your slots and target them specifically when you use the component.

```vue
<!-- ChildComponent.vue -->
<template>
  <div>
    <header>
      <slot name="header"></slot>
    </header>
    <main>
      <slot></slot>
    </main>
    <footer>
      <slot name="footer"></slot>
    </footer>
  </div>
</template>

<!-- ParentComponent.vue -->
<template>
  <ChildComponent>
    <template #header>
      <h1>This is the header content.</h1>
    </template>
    <p>This is some main content.</p>
    <template #footer>
      <p>This is the footer content.</p>
    </template>
  </ChildComponent>
</template>
```

###### Fallback (default)  content

> Specify **fallback (i.e. default)  content** for a slot, to **be rendered only when the parent didn't provide any slot content. **

```vue
<button type="submit">
  <slot>
    Submit <!-- fallback content -->
  </slot>
</button>
```

Now when we use **<SubmitButton>** in a parent component, providing no content for the slot:

```vue
<SubmitButton />
```

This will render the fallback content, "Submit":

```vue
<button type="submit">Submit</button>
```

But if we provide content:

```vue
<SubmitButton>Save</SubmitButton>
```

Then the provided content will be rendered instead:

```vue
<button type="submit">Save</button>
```

###### Scoped Slots

![image-20231123161542948](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231123161542948.png)

> **Scoped slots** are a feature in Vue.js that **allow you to access child component data in the parent component**. 
>
> Just **like passing `props` to a component.**
>
> - Receive props using a single **Default scoped slot** by using `v-slot` directly on the child component tag:`v-slot="slotProps"`
> - **Named scoped slots** work similarly - slot props are accessible as the value of the `v-slot` directive: `v-slot:name="slotProps"`

```vue
<!-- ChildComponent.vue -->
<template>
  <div>
    <slot name="mySlot" :myData="childData"></slot>
  </div>
  <div>
    <slot :myData="childData"></slot>
  </div>
</template>

<script>
export default {
  data() {
    return {
      childData: 'Hello from child'
    }
  }
}
</script>

<!-- ParentComponent.vue -->
<template>
  <ChildComponent>
    <template v-slot:mySlot="slotProps">
      <p>{{ slotProps.myData }}</p>
    </template>
  </ChildComponent>
  <ChildComponent>
    <template v-slot="slotProps">
      <p>{{ slotProps.myData }}</p>
    </template>
  </ChildComponent>
</template>
```



## Vue Cli

### Installation

```bash
# 全局安装webpack

npm install webpack -g
```

![image-20221217223101795](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217223101795.png)

```bash
# 全局安装 vue脚手架

npm install -g @vue/cli-init

npm install --global vue-cli
```

![image-20221217223805568](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217223805568.png)

### Create a Project

```bash
vue create project-name
```

![image-20231126100513640](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231126100513640.png)

![image-20231126101228526](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20231126101228526.png)

## Vue-UI-Plugins

### Vue-ElementUI

https://element.eleme.cn/#/zh-CN

![image-20221217232802260](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217232802260.png)

#### npm 安装

推荐使用 npm 的方式安装，它能更好地和 [webpack](https://webpack.js.org/) 打包工具配合使用。

```shell
npm i element-ui -S
```

![image-20221217232916534](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217232916534.png)

![image-20221217232937271](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217232937271.png)

#### 引入 Element

你可以引入整个 Element，或是根据需要仅引入部分组件。我们先介绍如何引入完整的 Element。

#### [¶](https://element.eleme.cn/#/zh-CN/component/quickstart#wan-zheng-yin-ru) 完整引入

在 main.js 中写入以下内容：

```javascript
import Vue from 'vue';
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
import App from './App.vue';

Vue.use(ElementUI);

new Vue({
  el: '#app',
  render: h => h(App)
});
```

以上代码便完成了 Element 的引入。需要注意的是，样式文件需要单独引入。

![image-20221217233124406](https://eddie-typora-image.oss-cn-shenzhen.aliyuncs.com/typora-user-images/image-20221217233124406.png)
