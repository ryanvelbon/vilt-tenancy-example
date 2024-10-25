<script setup>
import { Head, Link } from '@inertiajs/vue3';

defineProps({
    users: Array,
});


</script>

<template>
    <Head title="Welcome" />
    <div class="h-screen bg-gray-50 text-black/50 dark:bg-black dark:text-white">
        <header>
            <nav class="-mx-3 flex flex-1 justify-end px-8 py-2">
                <Link
                    v-if="$page.props.auth.user"
                    :href="route('dashboard')"
                    class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                >
                    Dashboard
                </Link>

                <template v-else>
                    <Link
                        :href="route('login')"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        Log in
                    </Link>

                    <Link
                        :href="route('register')"
                        class="rounded-md px-3 py-2 text-black ring-1 ring-transparent transition hover:text-black/70 focus:outline-none focus-visible:ring-[#FF2D20] dark:text-white dark:hover:text-white/80 dark:focus-visible:ring-white"
                    >
                        Register
                    </Link>
                </template>
            </nav>
        </header>
        <main class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-8">
            <section class="rounded p-4 bg-white/10 space-y-4">
                <h1 class="text-xl font-bold">Welcome!</h1>

                <p>This is a tenant route page. It is inaccessible from the central domain.</p>

                <p>Notice how tenants routes are automatically resolved for the current tenant.</p>

                <a :href="route('example')">Example</a><br>
            </section>

            <section class="rounded p-4 bg-white/10">
                <h2 class="text-xl font-bold">Users</h2>
                <p>Here are all the users of this tenant.</p>
                <ul class="mt-6 text-xs">
                    <li v-for="user in users" :key="user.id">{{ user.name }}</li>
                </ul>
            </section>
        </main>
    </div>
</template>
