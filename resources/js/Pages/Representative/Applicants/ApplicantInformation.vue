<script setup>
import AuthenticatedLayout from "@/Layouts/AuthenticatedLayout.vue";
import { Head, Link } from "@inertiajs/vue3";

defineProps(["applicant"]);
</script>

<template>
    <Head title="Applicant Information" />
    <AuthenticatedLayout>
        <section
            v-if="applicant.approve === 0 && applicant.reject === 0"
            class="px-4 pt-5 pb-8 mx-auto sm:px-6 x"
        >
            <header class="flex items-center justify-between">
                <div class="flex items-center gap-2">
                    <div
                        class="flex items-center justify-center w-8 h-8 text-xs tracking-tighter text-white bg-indigo-600 rounded-full"
                    >
                        {{ applicant.first_name.charAt(0) }}
                        {{ applicant.last_name.charAt(0) }}
                    </div>
                    <div>
                        <div class="flex items-center gap-2">
                            <h2>
                                {{ applicant.first_name }}
                                {{ applicant.last_name }}
                            </h2>
                            <div
                                class="px-4 py-1 text-xs text-white bg-indigo-700 rounded"
                            >
                                Applicant
                            </div>
                        </div>

                        <a
                            target="__blank"
                            :href="`mailto:${applicant.email}`"
                            class="block text-xs text-indigo-600 underline"
                            >{{ applicant.email }}</a
                        >
                    </div>
                </div>

                <div>
                    <Link
                        :href="route('applicants.index')"
                        preserve-scroll
                        class="inline-flex items-center px-4 py-2 text-sm font-medium text-gray-700 bg-white border border-gray-300 rounded-md shadow-sm hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500"
                    >
                        Back
                    </Link>
                </div>
            </header>

            <div class="grid grid-cols-1 mt-10 gap-x-6 gap-y-4 sm:grid-cols-6">
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Scholarship</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.scholarship.scholarshipName }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Student ID</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.student_id }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Campus</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.campus }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Degree Program</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.degree }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Phone Number</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.average }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Address</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.admission_test_score }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Email Address</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.email }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >First Name</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.first_name }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Middle Name</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.middle_name }}
                        </div>
                    </div>
                </div>
                <div class="sm:col-span-3">
                    <span
                        class="block text-sm font-medium leading-6 text-gray-900"
                        >Last Name</span
                    >
                    <div class="mt-2">
                        <div
                            class="block px-4 w-full rounded-md border-0 py-1.5 text-gray-900 shadow-sm ring-1 ring-inset ring-gray-300 placeholder:text-gray-400 focus:ring-2 focus:ring-inset focus:ring-indigo-600 sm:text-sm sm:leading-6"
                        >
                            {{ applicant.last_name }}
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <section v-else class="relative px-4 pt-5 pb-8 mx-auto sm:px-6 x">
            <p class="max-w-xl mx-auto text-center sm:w-full">
                The application form of this applicant has undergone a
                processing step, resulting in the information becoming
                inaccessible for viewing.
            </p>
            <span class="absolute stamp right-4 top-20 opacity-10"
                >application reviewed</span
            >
        </section>
    </AuthenticatedLayout>
</template>
