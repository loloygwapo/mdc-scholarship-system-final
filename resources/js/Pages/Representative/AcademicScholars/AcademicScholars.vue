<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, Link } from "@inertiajs/vue3";
import ApproveWithRemarks from "./ApproveWithRemarks.vue";
import RejectWithRemarks from "./RejectWithRemarks.vue";

defineProps(["scholars"]);

const isGraduated = (scholar) => {
    const currentYear = new Date().getFullYear();
    const enrollmentYear = parseInt(scholar.student_id.substring(0, 2)) + 2000;
    const courseDuration = 4;
    return currentYear - enrollmentYear >= courseDuration;
};
</script>

<template>
    <Head title="Academic Scholars" />
    <AuthenticatedLayout>
        <header class="flex items-center justify-between border-b border-slate-100">
            <h2 class="text-lg font-semibold text-slate-800">Academic Scholars</h2>
        </header>

       <div class="flex justify-end mt-4 space-x-2">

    <!-- First Page Link -->
    <Link
        v-if="scholars.first_page_url"
        :href="scholars.first_page_url"
        class="px-3 py-1 text-sm text-center border rounded"
        :class="{
            'pointer-events-none opacity-50': scholars.current_page === 1,
            'text-gray-700 hover:bg-gray-100': scholars.current_page !== 1,
        }"
        aria-label="First page"
    >
        <span>&laquo;&laquo;</span>
    </Link>

    <div class="flex items-center gap-1">
        <!-- Previous Button -->
        <Link
            v-if="scholars.prev_page_url"
            :href="scholars.prev_page_url"
            class="px-3 py-1 text-sm border rounded min-w-[80px] text-center hover:bg-gray-100"
            :class="{ 'pointer-events-none opacity-50': !scholars.prev_page_url }"
        >
            <span class="inline-flex items-center">← Previous</span>
        </Link>

        <!-- Current Page Display -->
        <span
            class="px-3 py-1 text-sm border rounded min-w-[32px] text-center bg-indigo-500 text-white"
        >
            {{ scholars.current_page }}
        </span>

        <!-- Next Button -->
        <Link
            v-if="scholars.next_page_url"
            :href="scholars.next_page_url"
            class="px-3 py-1 text-sm border rounded min-w-[80px] text-center hover:bg-gray-100"
            :class="{ 'pointer-events-none opacity-50': !scholars.next_page_url }"
        >
            <span class="inline-flex items-center">Next →</span>
        </Link>
    </div>

    <!-- Last Page Link -->
    <Link
        v-if="scholars.last_page_url"
        :href="scholars.last_page_url"
        class="px-3 py-1 text-sm text-center border rounded"
        :class="{
            'pointer-events-none opacity-50': scholars.current_page === scholars.last_page,
            'text-gray-700 hover:bg-gray-100': scholars.current_page !== scholars.last_page,
        }"
        aria-label="Last page"
    >
        <span>&raquo;&raquo;</span>
    </Link>
</div>



        <div v-if="scholars.data.length === 0" class="flex flex-col items-center justify-center gap-8 mt-16">
            <img class="h-60" src="/images/empty-state/empty-illustration.svg" />
            <h2 class="text-center uppercase sm:text-xl">No Scholars at the Moment</h2>
        </div>

        <div v-else class="relative mt-6 overflow-x-auto shadow-md sm:rounded-lg">
            <table class="w-full text-sm text-left text-gray-500">
                <thead class="text-xs text-gray-700 uppercase bg-indigo-50">
                    <tr>
                        <th scope="col" class="px-6 py-3">Student ID</th>
                        <th scope="col" class="px-6 py-3">Scholar's Name</th>
                        <th scope="col" class="px-6 py-3">Scholarship</th>
                        <th scope="col" class="px-6 py-3">Action</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="scholar in scholars.data" :key="scholar.id" class="bg-white border-b">
                        <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap">
                            {{ scholar.student_id }}
                        </th>
                        <td class="px-6 py-4">
                            {{ scholar.last_name }}, {{ scholar.first_name }} {{ scholar.middle_name?.charAt(0) }}.
                        </td>
                        <td class="px-6 py-4">
                            {{ scholar.scholarship.scholarshipName }}
                        </td>
                        <td class="flex items-center gap-1 px-6 py-4">
                            <div
                                v-if="scholar.approve === 1"
                                class="px-3 py-1.5 font-medium text-xs inline-flex items-center justify-center border border-transparent rounded leading-5 shadow-sm transition duration-150 ease-in-out bg-indigo-700 hover:bg-indigo-600 text-white"
                            >
                                Approved
                            </div>
                            <div
                                v-else-if="scholar.reject === 1"
                                class="px-3 py-1.5 font-medium text-xs inline-flex items-center justify-center border border-transparent rounded leading-5 shadow-sm transition duration-150 ease-in-out bg-red-700 hover:bg-red-600 text-white"
                            >
                                Rejected
                            </div>
                            <div v-else class="flex items-center gap-1">
                                <ApproveWithRemarks :scholar="scholar" />
                                <RejectWithRemarks :scholar="scholar" />
                            </div>
                            <Link
                                :href="route('academic-scholars.show', { id: scholar.id })"
                                class="inline-flex items-center justify-center px-3 py-2 text-sm font-medium leading-5 text-white transition duration-150 ease-in-out bg-indigo-700 border border-transparent rounded shadow-sm hover:bg-indigo-600"
                            >
                                <span class="text-xs xs:block">More Details</span>
                            </Link>
                        </td>
                    </tr>
                </tbody>
            </table>




        </div>
    </AuthenticatedLayout>
</template>
