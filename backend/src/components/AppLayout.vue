<template>
    <div class="min-h-full flex">
        <!-- sidebar -->
        <Sidebar :class="{'-ml-[200px]' : !sidebarOpened}"/>
        <!-- end sidebar -->
        <div class="flex-1">
            <TopHeader @toggle-sidebar="toggleSidebar"/>
            <!-- content -->
            <main class="p-6">

                <router-view></router-view>


            </main>
            <!-- end content -->
        </div>

    </div>
</template>

<script setup>
import { ref } from "vue";
import Sidebar from "../components/Sidebar.vue"
import TopHeader from "./TopHeader.vue";
const { title } = defineProps({
    title: String
})

const sidebarOpened = ref(true)

function toggleSidebar(){
   sidebarOpened.value = !sidebarOpened.value
}


</script>