<script setup lang="ts">

// const vvv:string = '<div style="color:red">安安安安安安安安安安</div>';

// const id: string = 'a'
// const Redstyle = {
//   color: 'red',
//   border: '30px solid red',
//   backgroundColor: "white"
// }

// const Bluestyle = {
//   color: 'blue',
//   border: '30px solid blue',
//   backgroundColor: "red"
// }

// const Whitestyle = {
//   color: 'white',
//   border: '30px solid white',
//   backgroundColor: "blue",
// }

// const condition: string = 'red'
// const Cls:boolean = false
// const arr:string[] = ['a', 'b', 'c', 'd', 'e', 'f']
// arr.splice(2,2,'DDD','ccc');
import { ref, reactive } from 'vue';
// const Tagname = ref('');

interface PLAYERS {
  id: number
  name: string
  age: null | number
  email: string
}


const items = reactive<PLAYERS[]>([
  { id: 1, name: 'John', age: 25, email: 'john@example.com' },
  { id: 2, name: 'Jane', age: 30, email: 'jane@example.com' },
  { id: 3, name: 'Bob', age: 40, email: 'bob@example.com' }
]);



const addPlayer = reactive({
  name:'',
  age: null,
  email:''
});

function submit() {
  const newitems = {
  id : items.length + 1,
  name : addPlayer.name,
  age : addPlayer.age,
  email : addPlayer.email
}
  console.log('姓名:', newitems.name);
  items.push(newitems);
}


</script> 

<template>
  <div>
    <form>
      <input type="text" v-model="addPlayer.name" placeholder="请输入姓名" />
      <input type="number" v-model="addPlayer.age" placeholder="请输入年龄" />
      <input type="text" v-model="addPlayer.email" placeholder="请输入email" />
      <button v-on:click.prevent="submit">提交</button>
    </form>
  </div>
  <div v-for="item in items" :key="item.id">
    {{ item.id }}：{{ item.name }}：{{ item.age }}：{{ item.email }}
  </div>
  <div>

    <!-- <input type="text" v-model="Tagname" /> -->
    <!-- {{ Tagname }} -->

    <!-- <div v-for="(item,index) in arr">
                        {{ index }} - {{ item }}
                        </div> -->
    <!-- <div v-if="condition == 'red'" :style="[Redstyle,TextStyle]">我是紅色class</div>
                              <div v-else-if="condition == 'blue'" :style="Bluestyle">我是藍色class</div>
                              <div v-else :style="[Whitestyle,TextStyle]">nothing</div>
                              <div :style="[Cls ? Bluestyle: Redstyle]">三元運算測試</div> -->
  </div>
</template>

<style scoped></style>
