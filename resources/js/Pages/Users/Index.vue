<template>
    <Head title="Users"/>
    <div class="flex justify-between mb-6">
        <div class="flex items-center">
            <h1 class="text-3xl">Users</h1>
            <Link href="/users/create" class="text-blue-500 ml-3">New User</Link>
        </div>
        <input v-model="search" type="text" placeholder="Search..." class="border px-2 rounded-lg">
    </div>
    <div class="overflow-x-auto relative shadow-md sm:rounded-lg">
        <table class="w-full text-sm text-left text-gray-500 dark:text-gray-400">
            <tbody>
                <tr v-for="user in users.data" :key="user.id" class="bg-white border-b dark:bg-gray-900 dark:border-gray-700">
                    <td scope="row" class="py-4 px-6 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        {{ user.name }}
                    </td>
                    <td class="py-4 px-6">
                        <Link :href="`/users/${user.id}/edit`" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">
                            Edit
                        </Link>
<!--                        LINK :href="`/users/${user.id}/edit`" class="font-medium text-blue-600 dark:text-blue-500 hover:underline">Edit</LINK>-->
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
    <Pagination :links="users.links" class="mt-6"/>
</template>

<script setup>
import Pagination from "../../Shared/Pagination";
import {ref, watch} from "vue";
import {Inertia} from "@inertiajs/inertia";

let props = defineProps({
    users:Object,
    filters:Object
})

let search = ref(props.filters.search);

watch(search,value => {
    Inertia.get('/users',{search:value},{
        preserveState:true,
        replace:true
    });
})
</script>
<style scoped>

</style>
