<template>
    <titulo texto="Ruta con Parámetros" />
    <!--<button @click= "consumirAPI"> Consumir API </button> -->
     <div v-for="item in arrayBlog" :key="item.id">
        <router-link :to="`/blog/${item.id}`"> 
        {{item.title}} 
        </router-link>
        
    </div>  
</template>
<script>
import Titulo from '../components/Titulo.vue'
export default {
    components: {
        Titulo
    },
    data() {
        return {
            arrayBlog: []
        }
    },
    methods: {
       async consumirAPI() {
           try {
               const data = await fetch('https://jsonplaceholder.typicode.com/posts')
               const array = await data.json()
               console.log(array)
               this.arrayBlog = array;
           } catch (error) {

           }
        }
    },
    created() {
        this.consumirAPI()
    }
}
</script>
<style>
    
</style>