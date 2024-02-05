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
  </div>
</template>

<script>
import { computed, ref, watchEffect, watch } from 'vue';
import PostList from '@/components/PostList.vue';
import getPosts from '../composables/getPosts';

export default {
  name: 'HomeView',
  components: { PostList },
  setup() {
    // load();
    const { posts, error, load } = getPosts()

    load()

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
