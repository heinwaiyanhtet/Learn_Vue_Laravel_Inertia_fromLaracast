<template>
    <Layout>
        <h1 class="text-3xl">Users</h1>
        <div style="margin-top: 800px">
            <p>The current time is {{ time }} . </p>
            <Link href="/users" class="text-blue-500" preserve-scroll>
                Refresh
            </Link>
        </div>
    </Layout>
</template>

<script setup>
import {Link} from "@inertiajs/inertia-vue3";
import Layout from "../Shared/Layout";

defineProps({
    time:String
});
</script>
<style scoped>

</style>
