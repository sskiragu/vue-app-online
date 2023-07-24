<template>
  <div class="home">
    <h1>Welcome home</h1>
    <h1>Counter</h1>

    <div>
      <button @click.prevent="increment">Increment</button>
      <button @click.prevent="decrement">Decrement</button>
      <p>Count: {{ count }}</p>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';


// Options API - Object oriented
// export default {
//   data(){
//     return {
//       count: 0
//     }
//   },
//   methods: {
//     increment(){
//       this.count++
//     },
//     decrement(){
//       this.count--
//     }
//   }
// }


// Composition API - functional

export default {
  setup(){
    const count = ref(0)

    function increment(){
      count.value++
    }

    function decrement(){
      count.value--
    }

    return { count, increment, decrement }
  }
}

</script>
