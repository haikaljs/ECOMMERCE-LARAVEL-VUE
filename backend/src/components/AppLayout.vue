<template>
 <div class="min-h-full flex">
    <!-- sidebar -->
   <Sidebar/>
    <!-- end sidebar -->
    <div class="flex-1">
        <header class="h-8 shadow bg-white">Header</header>
        <!-- content -->
        <main>
            <router-view></router-view>
        </main>
        <!-- end content -->
    </div>
    
 </div>
</template>

<script setup>
import Sidebar from "../components/Sidebar.vue"
const {title} = defineProps({
    title: String
})
</script>