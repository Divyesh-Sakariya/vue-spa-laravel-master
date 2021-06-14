<template>
    <div>
        <div v-if="user" class=" p-5">
        Name: {{user.name}} <br>
        Email: {{user.email}}<br><br>
        <button class="text-white bg-red-600 border-0 py-2 px-8 focus:outline-none hover:bg-red-700 rounded text-lg" @click.prevent="logout">Logout</button>
        </div>

    </div>
</template>
<script>
export default {
    data(){
        return{
            user: null
        }
    },
    methods:{
        logout(){
            axios.post('/api/logout').then(()=>{
                this.$router.push({ name: "Home"})
            })
        }
    },
    mounted(){
        axios.get('/api/user').then((res)=>{
            this.user = res.data
        })
    }
}
</script>