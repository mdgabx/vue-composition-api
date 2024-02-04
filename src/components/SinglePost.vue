<template>
 <h2>{{ post.title }}</h2>
 <p>{{ snippets }}</p>

</template>

<script>
import { computed } from 'vue'
export default {
    props: ['post'],
    setup(props) {

        const snippets = computed(() => {
            return props.post.body.substring(0, 100) + '...'
        })

        return { snippets }
    }
}
</script>

<style>

</style>