<template>
  <Head title="Create User" />

  <h1 class="text-3xl">Create New User</h1>

  <form @submit.prevent="submit" class="max-w-md mx-auto mt-8">
      <div class="mb-6">
          <label for="name" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Name</label>
          <input v-model="form.name" type="text" class="w-full p-2 border border-gray-400" name="name" id="name" required>
          <div v-if="errors.name" v-text="errors.name" class="mt-1 text-xs text-red-500"></div>
      </div>

      <div class="mb-6">
          <label for="email" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Email</label>
          <input v-model="form.email" type="email" class="w-full p-2 border border-gray-400" name="email" id="email" required>
          <div v-if="errors.email" v-text="errors.email" class="mt-1 text-xs text-red-500"></div>
      </div>

      <div class="mb-6">
          <label for="password" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Password</label>
          <input v-model="form.password" type="password" class="w-full p-2 border border-gray-400" name="password" id="password" required>
          <div v-if="errors.password" v-text="errors.password" class="mt-1 text-xs text-red-500"></div>
      </div>

      <div class="mb-6">
          <button type="submit" class="px-4 py-2 text-white bg-blue-400 rounded hover:bg-blue-500">Submit</button>
      </div>
  </form>
</template>

<script setup>
    import { Inertia } from "@inertiajs/inertia";
    import { reactive } from "@vue/reactivity";

    defineProps({
        errors: Object
    })

    let form = reactive({
        name: '',
        email: '',
        password: ''
    });

    let submit = () => {
        Inertia.post('/users', form);
    }
</script>
