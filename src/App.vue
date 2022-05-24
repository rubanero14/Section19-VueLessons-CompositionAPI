<template>
  <section class="container">
    <h3>{{ age }}</h3>
    <h4>{{ user }}</h4>
    <button @click="addAge">Change age</button>
    <div>
      <input type="text" placeholder="First Name" v-model="firstName"/>
      <input type="text" placeholder="Last Name" v-model="lastName"/>
    </div>
  </section>
</template>

<script setup>
import { ref,computed, watch } from 'vue';

// const user = ref('Raj');
const age = ref(35);
const firstName = ref('');
const lastName = ref('');

const user = computed(function(){
  return firstName.value + ' ' + lastName.value;
});

watch([age, user], function(newValues, oldValues){
  console.log('Old age value: '+ oldValues[0]);
  console.log('New age value: '+ newValues[0]);
  console.log('Old name value: '+ oldValues[1]);
  console.log('New name value: '+ newValues[1]);
});

// const user = reactive({
//   name: 'Raj',
//   age: 35,
// });

function addAge(){
  return age.value += 10;
}

// setTimeout(
//   function(){
//     let names = ['Sharm', 'Akshu'];
//     let ages = [34,3];
//     const Rand = Math.round(Math.random())
//     user.name = names[Rand];
//     user.age = ages[Rand];
//   }
// , 2000)
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.container {
  margin: 3rem auto;
  max-width: 30rem;
  border-radius: 12px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  padding: 1rem;
  text-align: center;
}
</style>