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

interface Player {
  id: number
  name: string
  age: null | number
  email: string
}


const items = reactive<Player[]>([
  { id: 1, name: 'John', age: 25, email: 'john@example.com' },
  { id: 2, name: 'Jane', age: 30, email: 'jane@example.com' },
  { id: 3, name: 'Bob', age: 40, email: 'bob@example.com' }
]);



const Addplayer = reactive({
  name: '',
  age: null,
  email: ''
});

function submit() {

  if (Addplayer.name != '' && Addplayer.age != null && Addplayer.email != '') {
    const newitems = {
      id: items.length + 1,
      name: Addplayer.name,
      age: Addplayer.age,
      email: Addplayer.email
    }
    items.push(newitems);

  }
  else {
    alert('请填写完整信息');
  }
}

let list = reactive<string[]>([]);
const addlist = () => {
  list.push('bob', 'bob@example.com');
};

interface FilterFunction {
  (value: number): number;
}

const isEven: FilterFunction = (value) => value % 2;

console.log(isEven(11)); // true

// function teayea<T>(a:T,b:T):Array<T>{
//   return [a,b];
// }

//使用 <T> 可以使後續需要帶入的數自行判斷類型




// interface Axxsxx {
//   name: string
//   age: number
//   demo?:string
//   // [propName:string]:any //接取任意屬性
// }

// let a: Axxsxx = {
//   name:'awa',
//   age:12,
//   // demo:'AAAA'
// }

// const arr: [x: number, y?: boolean] = [0, false]

// arr.push(1)
// console.log(arr)


//
</script> 

<template>
  <!-- <div> -->
  <!-- <form>
      <input type="text" v-model="Addplayer.name" placeholder="请输入姓名" />
      <input type="number" v-model="Addplayer.age" placeholder="请输入年龄" />
      <input type="text" v-model="Addplayer.email" placeholder="请输入email" />
      <button @click.prevent="submit">提交</button>
    </form> -->
  <!-- </div>
    <div v-for="item in items" :key="item.id">
    {{ item.id }}：{{ item.name }}：{{ item.age }}：{{ item.email }}
  </div> -->
  <div v-for="item in list">
    {{ item }}
  </div>
  <button @click="addlist">add</button>

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
