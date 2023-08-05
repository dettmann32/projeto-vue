<template>
    <header >
        <nav class="flex bg-[#222] border-solid border-b-4 border-purple-[#111] py-[15px] px-[50px] items-center justify-end ">
        <router-link to="/" class="m-auto ml-0">
            <img :src="logo" :alt="alt" id="logo" class="w-[40px] h-[40px]">
        </router-link>
        <router-link to="/" class="text-[#fcba03] m-[12px] transition hover:text-white">Home</router-link> |
        <router-link to="/Pedidos" class="text-[#fcba03] m-[12px] transition hover:text-white">Pedidos</router-link>
        </nav>
    </header>
</template>

<script>
    export default {
        name: "NavBar",
        data(){
            return
        },
        props:['logo','alt']
    }
</script>

<style>

</style>