<template>
  <div class="home">
    <div v-if="error">
      {{ error }}
    </div>
    <div v-if="posts.length">
      <PostList :posts="posts" />
    </div>
    <div v-else>
      Loading...
    </div>
  
    <!-- <p ref="p">Name {{ name }} and {{ age }}</p>
    <button @click="handleClick">Click</button>
    <input type="text" v-model="name" />
   -->
   <!-- <input type="text" v-model="search" />
   <p>{{ search }}</p>
   <div v-for="name in matchingNames" :key="name">
    {{ name }}
   </div>
   <button @click="handleStop">stop watch</button> -->

  
  </div>
</template>

<script>
import { computed, ref, watchEffect, watch } from 'vue';
import PostList from '@/components/PostList.vue';

export default {
  name: 'HomeView',
  components: { PostList },
  setup() {
    const posts = ref([])
    const error = ref(null)

    const load = async () => {
      try {
        let data = await fetch('http://localhost:3000/posts')
        if(!data.ok) {
          throw Error('no data available')
        }

        posts.value = await data.json()

      } catch (err) {
        error.value = err.message
      }
    }

    load();

    return { posts, error }

    // const p = ref(null)

    // const name = ref('Mario');
    // const age = ref(10);

    // const handleClick = () => {
    //   console.log(p, p.value)
    //   name.value = 'test'
    //   age.value = 25
    // }

    // return { name, age, handleClick, p }

    // const names = ref(['max', 'alhihi', 'nahida', 'kaeya'])
    // const search = ref('')

    // const stopWatch = watch(search, () => {
    //   console.log('run')
    // })

    // const stopEffect = watchEffect(() => {
    //   console.log('rada', search.value)
    // })

    // const handleStop = () => {
    //   stopWatch()
    //   stopEffect()
    // }
    
    // const matchingNames = computed(() => {
    //   return names.value.filter((item) => item.includes(search.value))
    // })

    // return { names, search, matchingNames, handleStop }

  }
}
</script>
