<template>
    <app-layout>
        <div class="flex  bg-gray-200">
            <Sidebar/>
            <ProductBox/>
        </div>
    </app-layout>
</template>
<script>
    import AppLayout from '@/Layouts/AppLayout'
    import Sidebar from '@/Components/Sidebar.vue'
    import ProductBox from '@/Components/ProductBox.vue'


    export default {
        components: {
            AppLayout,
            ProductBox,
            Sidebar
        },
    }
</script>
