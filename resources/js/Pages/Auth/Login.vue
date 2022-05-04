<template>
    <Head title="Login Page" />

  <main class="grid min-h-screen place-items-center">
      <section class="max-w-md p-8 mx-auto mt-8 bg-white border rounded-xl">
          <h1 class="text-3xl">Login</h1>

        <form @submit.prevent="submit">

            <div class="mb-6">
                <label for="email" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Email</label>
                <input v-model="form.email" type="email" class="w-full p-2 border rounded" name="email" id="email">
                <div v-if="form.errors.email" v-text="form.errors.email" class="mt-1 text-xs text-red-500"></div>
            </div>

            <div class="mb-6">
                <label for="password" class="block mb-2 text-xs font-bold text-gray-700 uppercase">Password</label>
                <input v-model="form.password" type="password" class="w-full p-2 border rounded" name="password" id="password">
                <div v-if="form.errors.password" v-text="form.errors.password" class="mt-1 text-xs text-red-500"></div>
            </div>

            <div class="mb-6">
                <button type="submit" class="px-4 py-2 text-white bg-blue-400 rounded hover:bg-blue-500" :disabled="form.processing">Log In</button>
            </div>
        </form>
      </section>
  </main>
</template>

<script>
export default {
    layout: null
}
</script>

<script setup>
import { useForm } from '@inertiajs/inertia-vue3'
let form = useForm({
    email: '',
    password: ''
})

let submit = () => {
    form.post('/login');
}
</script>
