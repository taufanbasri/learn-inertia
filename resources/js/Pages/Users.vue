<template>
  <layout>
    <h1 class="text-3xl">Users</h1>

    <div style="margin-top: 600px">
        <p>The current time is {{ time }}.</p>

        <Link href="/users"
                class="text-blue-500"
                preserve-scroll
        >
                Refresh
        </Link>
    </div>
  </layout>
</template>

<script setup>
import { Link } from "@inertiajs/inertia-vue3";
import Layout from '../Shared/Layout.vue';

defineProps({
    time: String
})
</script>

<style>

</style>
