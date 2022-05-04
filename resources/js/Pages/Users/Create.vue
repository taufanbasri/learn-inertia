<template>
  <Head title="Create User" />

  <h1 class="text-3xl">Create New User</h1>

  <form @submit.prevent="submit" class="max-w-md mx-auto mt-8">
      <div class="mb-6">
          <label for="name" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Name</label>
          <input v-model="form.name" type="text" class="w-full p-2 border border-gray-400" name="name" id="name">
          <div v-if="form.errors.name" v-text="form.errors.name" class="mt-1 text-xs text-red-500"></div>
      </div>

      <div class="mb-6">
          <label for="email" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Email</label>
          <input v-model="form.email" type="email" class="w-full p-2 border border-gray-400" name="email" id="email">
          <div v-if="form.errors.email" v-text="form.errors.email" class="mt-1 text-xs text-red-500"></div>
      </div>

      <div class="mb-6">
          <label for="password" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Password</label>
          <input v-model="form.password" type="password" class="w-full p-2 border border-gray-400" name="password" id="password">
          <div v-if="form.errors.password" v-text="form.errors.password" class="mt-1 text-xs text-red-500"></div>
      </div>

      <div class="mb-6">
          <button type="submit" class="px-4 py-2 text-white bg-blue-400 rounded hover:bg-blue-500" :disabled="form.processing">Submit</button>
      </div>
  </form>
</template>

<script setup>
    import { useForm } from "@inertiajs/inertia-vue3";

    let form = useForm({
        name: '',
        email: '',
        password: ''
    });

    let submit = () => {
        form.post('/users');
    }
</script>
