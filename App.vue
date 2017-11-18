<template>
  <div>
    {{hello}}
    <p v-html="hello"></p>
    <p v-text="hello"></p>
    {{num+1}}
    {{status?'s':'f'}}
    <u1>
    <p v-for="item in list">{{item.name}}-{{item.price}}</p>
    </u1>
    <button v-on:click="addItem">addItem</button>
    <button @click="toggle">toggle</button>
    <input @keydown.enter="onKeydown">
    <u2>
    <li v-for="(item,index) in list":class="{odd:index %2}">{{item.name}}-{{item.price}}-{{index}}</li>
    </u2>
    <u3>
    <li v-for="value in objlist">{{value}}</li>
    </u3>
    <u4>
    <li v-for="(value,key) in objlist">{{key+value}}</li>
    </u4>

    <componentA v-for="(value,key) in objlist"></componentA>

    <componentA :dataA="dataA"></componentA>
    <a v-bind:href="link" :title="hello">to baidu</a>
    <a v-bind:class="[classA,classB]">to baidu</a>
    <a v-if="isPartA">partA</a>
    <a v-show="!isPartA">partB</a>

    <input type="text" name="" v-model.lazy="myVal">
    {{myVal}}

<input type="checkbox" name="" value="apple" v-model="mv">
<label>apple</label>
<input type="checkbox" name="" value="banana" v-model="mv">
<label>banana</label>
<input type="checkbox" name="" value="orange" v-model="mv">
<label>orange</label>
{{mv}}

<input type="radio" name="" value="1" v-model="mv1">
<label>apple</label>
<input type="radio" name="" value="2" v-model="mv1">
<label>banana</label>
<input type="radio" name="" value="3" v-model="mv1">
<label>orange</label>
{{mv1}}

<select v-model="mv2">
<option value="0">apple</option>
<option value="1">banana</option>
<option value="2">orange</option>
</select>
{{mv2}}

<select v-model="mv3">
<option v-for="item in options" :value="item.value">{{item.name}}</option>
</select>

{{mv3}}

<v-select :option="options"></v-select>

<input type="text" v-model="m">
{{mvn}}
{{gtm()}}


  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'
import componentA from './components/apple.vue'
import vSelect from './components/vSelect.vue'
import Vue from 'vue'
export default {
components:{componentA,vSelect},
  data(){
  return{
  m:'',
  myVal:'',
  mv1:'2',
  mv2:1,
  mv3:3,
  mv:[],
  hello:'<span><img>hello world</span>',
  link:'http://www.baidu.com',
  isPartA:true,
  dataA:'dta',
  classA:'hello',
  classB:'world',
  options:[
    {
    name:'apple',
    value:0
    },
    {
    name:'banana',
    value:1
    }
  ],
  className:{
'red-font':true,
'blue-font':false
  },
  num : 1,
  status:true,
  list:[
  {
  name:'apple',
  price:1
  },
  {
  name:'banana',
  price:2
  }
  ],
  objlist:{
  name:'apple',
  price:1,
  color:'red',
  weight:14
  }
  }
  },
    computed:{
    mvn(){
    return this.m.replace(/\d/g,'')
    }
    },
  methods:{
  gtm(){
  return this.m.replace(/\d/g,'')
  },
  addItem(){
  Vue.set(this.list,1,{name:'pi',price:123}),
  this.list.push({
  name:'pinaapple',
  price:234
  })
  },
  toggle(){
  this.isPartA = !this.isPartA
  },
  onKeydown(){
  this.isPartA = !this.isPartA
  }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
