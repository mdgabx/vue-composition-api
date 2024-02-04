<template>
  <div class="home">
    <!-- <p ref="p">Name {{ name }} and {{ age }}</p>
    <button @click="handleClick">Click</button>
    <input type="text" v-model="name" />
   -->
   <input type="text" v-model="search" />
   <p>{{ search }}</p>
   <div v-for="name in matchingNames" :key="name">
    {{ name }}
   </div>

  </div>
</template>

<script>
import { computed, ref } from 'vue';

export default {
  name: 'HomeView',
  setup() {
    // const p = ref(null)

    // const name = ref('Mario');
    // const age = ref(10);

    // const handleClick = () => {
    //   console.log(p, p.value)
    //   name.value = 'test'
    //   age.value = 25
    // }

    // return { name, age, handleClick, p }

    const names = ref(['max', 'alhihi', 'nahida', 'kaeya'])
    const search = ref('')

    const matchingNames = computed(() => {
      return names.value.filter((item) => item.includes(search.value))
    })

    return { names, search, matchingNames }

  }
}
</script>
