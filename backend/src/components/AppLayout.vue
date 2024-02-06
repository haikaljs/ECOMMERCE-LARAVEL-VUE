<template>
    <div class="min-h-full flex">
        <!-- sidebar -->
        <Sidebar />
        <!-- end sidebar -->
        <div class="flex-1">
            <TopHeader />
            <!-- content -->
            <main class="p-6">

                <router-view></router-view>


            </main>
            <!-- end content -->
        </div>

    </div>
</template>

<script setup>
import Sidebar from "../components/Sidebar.vue"
import TopHeader from "./TopHeader.vue";
const { title } = defineProps({
    title: String
})
</script>