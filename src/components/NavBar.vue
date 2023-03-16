<script setup>
import { ref } from 'vue'
const brand = ref('🏨 Fake Company Directory')
</script>



<template>
   <nav class="bg-red-400">
   <div class="wrapper">
   <RouterLink :to="{ name: 'Home' }" class="brand">
    <span class="brand-title">{{  brand }}</span>
   </RouterLink>
    <div class="menu">
        <a href="#" class="menu-item">Department</a>
        <a href="#" class="menu-item">Settings</a>
        <a href="#" class="menu-login">Logout</a>
    </div>
    </div>
    </nav>

</template>


<style scoped lang="postcss">
nav {
    @apply flex bg-purple-600 text-orange-400 h-20 ;
    .wrapper {
        @apply flex  items-center justify-between container mx-auto w-full;
        .brand {
            &-title {
                @apply text-2xl font-extrabold text-green-500;
            }
            
        }
        .menu {
            @apply flex gap-3;
            &-item {
                @apply hover:bg-green-500 hover:text-black px-1 py-1 rounded-md; 
            }
            &-login {
                @apply hover:bg-red-500 bg-green-500 hover:text-orange-400 px-1 py-1 rounded-md text-black;
            }
        }
    }
}
</style>