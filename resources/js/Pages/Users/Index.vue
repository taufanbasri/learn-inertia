<template>
    <Head title="Users"/>

    <div class="flex justify-between mb-6">
        <div class="flex items-center">
            <h1 class="text-3xl">Users</h1>

            <Link href="/users/create" class="ml-2 text-sm text-blue-500">New User</Link>
        </div>

        <input v-model="search" type="text" placeholder="Search..." class="px-2 border rounded-lg">
    </div>

    <div class="flex flex-col">
        <div class="-my-2 overflow-x-auto sm:-mx-6 lg:-mx-8">
            <div class="inline-block min-w-full py-2 align-middle sm:px-6 lg:px-8">
                <div class="overflow-hidden border-b border-gray-200 shadow sm:rounded-lg">
                    <table class="min-w-full divide-y divide-gray-200">
                        <tbody class="bg-white divide-y divide-gray-200">
                            <tr v-for="user in users.data" :key="user.id">
                                <td class="px-6 py-4 whitespace-nowrap">
                                    <div class="flex items-center">
                                        <div>
                                            <div class="text-sm font-medium text-gray-900">
                                                {{ user.name }}
                                            </div>
                                        </div>
                                    </div>
                                </td>

                                <td class="px-6 py-4 text-sm font-medium text-right whitespace-nowrap">
                                    <Link :href="`/users/${user.id}/edit`" class="text-indigo-600 hover:text-indigo-900">Edit</Link>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
    </div>

    <Pagination :links="users.links" class="mt-6" />
</template>

<script setup>
import { Inertia } from "@inertiajs/inertia"
import { ref } from "@vue/reactivity"
import { watch } from "@vue/runtime-core"
import Pagination from "../../Shared/Pagination.vue"
import debounce from "lodash/debounce"

let props = defineProps({
    users: Object,
    filters: Object
})

let search = ref(props.filters.search)

watch(search, debounce(function (value) {
    Inertia.get('/users', { search: value }, {
        preserveState: true,
        replace: true
    })
}, 300));
</script>
