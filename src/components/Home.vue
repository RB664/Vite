<template>
   <h1 class="mb-6 text-3xl font-extrabold">Home</h1>

   <p class="mb-6">Name in store is: {{ name }}</p>

   <input v-model="newName" type="text" class="p-2 m-4 border border-gray-600 rounded" />


   <router-link to="/about">
       <button @click="saveName"  class="p-2 text-white bg-indigo-600">Submit</button>
   </router-link>
</template>

<script setup>
import { computed, ref } from 'vue'
import { useStore } from 'vuex'
import { useRouter} from 'vue-router'
const store = useStore()
const router = useRouter

const name = computed(() => {
    return store.state.user.name
})

const newName = ref('')
function saveName() {
    store.dispatch('saveName', newName.value)
    newName.value = ''
    router.push('/about')
}
</script>

<style>

</style>