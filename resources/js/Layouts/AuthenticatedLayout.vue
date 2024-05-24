<script setup>
import { ref } from 'vue';
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import Dropdown from '@/Components/Dropdown.vue';
import DropdownLink from '@/Components/DropdownLink.vue';
import NavLink from '@/Components/NavLink.vue';
import ResponsiveNavLink from '@/Components/ResponsiveNavLink.vue';
import { Link } from '@inertiajs/vue3';
import Navbar from '@/Partials/Navbar.vue'
import Sidebar from '@/Partials/Sidebar.vue'

const showingNavigationDropdown = ref(false);
</script>

<template>
    <Navbar />
    <div class="flex pt-16 overflow-hidden bg-gray-50 dark:bg-gray-900">
        <Sidebar />
        <div class="relative w-full h-full overflow-y-auto bg-gray-50 lg:ml-64 dark:bg-gray-900">
            <main class="px-4 pt-6">
                <header v-if="$slots.header">
                <div class="mb-4">
                    <slot name="header" />
                </div>
                </header>
                 <slot />
            </main>
        </div>
    </div>
</template>
