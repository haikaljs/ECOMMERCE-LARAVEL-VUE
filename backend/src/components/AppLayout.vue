<template>
    <!-- <div v-if="currentUser.id" class="min-h-full flex"> -->
         <div class="min-h-full flex">
        <!-- sidebar -->
        <Sidebar :class="{'-ml-[200px]' : !sidebarOpened}"/>
        <!-- end sidebar -->
        <div class="flex-1">
            <Navbar @toggle-sidebar="toggleSidebar"/>
            <!-- content -->
            <main class="p-6">

                <router-view ></router-view>


            </main>
            <!-- end content -->
        </div>

    </div>
    <!-- <div v-else class="min-h-full bg-gray-200 flex items-center justify-center"><h1>Loading...</h1></div> -->
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from "vue";
import Sidebar from "./Sidebar.vue";
import Navbar from "./Navbar.vue";
import store from "../store";
const { title } = defineProps({
    title: String
})

const sidebarOpened = ref(true)
const currentUser = computed(() => store.state.user.data)
function toggleSidebar(){
   sidebarOpened.value = !sidebarOpened.value
}

onMounted(() =>{
    if(window.outerWidth <= 768){
        sidebarOpened.value = false
    }
    window.addEventListener('resize', handleSidebarOpened)
})

onUnmounted(() => {
    store.dispatch('getUser')
    window.removeEventListener('resize', handleSidebarOpened)
})

function handleSidebarOpened(){
    if(window.outerWidth <= 768){
        sidebarOpened.value = false
    }else{
        sidebarOpened.value = true
    }
}

</script>