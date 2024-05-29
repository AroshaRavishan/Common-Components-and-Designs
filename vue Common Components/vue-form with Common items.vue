<script setup>
import { ref } from 'vue';
import { Link, useForm, router, usePage } from '@inertiajs/vue3';
import ClientTopSection from '../ClientTopSection.vue';
import PhotoSelect from '@/Components/ClientDashboard/CommonComponents/PhotoSelect.vue';
import InputLabel from '@/Components/ClientDashboard/CommonComponents/InputLabel.vue';
import TextInput from '@/Components/ClientDashboard/CommonComponents/TextInput.vue';
import CountryPicker from '@/Components/ClientDashboard/CommonComponents/CountryPicker.vue';
import InputSelect from '@/Components/ClientDashboard/CommonComponents/InputSelect.vue';
import FormSectionCustom from "@/Components/FormSectionCustom.vue";
import ClientPrimaryButton from '../CommonComponents/ClientPrimaryButton.vue';
import ClientSecondaryButton from '../CommonComponents/ClientSecondaryButton.vue';
import InputError from '@/Components/InputError.vue';

const props = defineProps({
    countries: {
        type: [],
        default: null,
    },
});

const statusList = ref([
    { id: '1', name: 'Active' },
    { id: '2', name: 'Inactive' },
    { id: '3', name: 'Blocked' },
]);

const password = ref('');
const showPassword = ref(false);

const togglePasswordVisibility = () => {
    showPassword.value = !showPassword.value;
};

const selectedCountry = () => {
    form.phone_number = '+' + props.countries.filter((country) => {
        return country.id === form.country_id
    })[0]['phonecode'];
}

</script>

<template>
    <div class="mt-5">
        <FormSectionCustom @submitted="createNewUser">
            <template #form>
                <div class="mt-2.5 bg-primary py-5 px-4 rounded-3 shade-class">
                    <PhotoSelect v-model="form.photo" />
                    <InputError class="mt-2" :message="form.errors.photo" />
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="">
                        <InputLabel value="First name*" />
                        <TextInput id="fname" v-model="form.fname" type="text" class="mt-1 block w-full"
                            autocomplete="fname" placeholder="eg. Michael" />
                        <InputError class="mt-2" :message="form.errors.fname" />
                    </div>
                    <div class="">
                        <InputLabel value="Last name*" />
                        <TextInput id="lname" type="text" v-model="form.lname" class="mt-1 block w-full"
                            autocomplete="lname" placeholder="eg. Jackson" />
                        <InputError class="mt-2" :message="form.errors.lname" />
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="">
                        <InputLabel value="Username*" />
                        <TextInput id="name" type="text" v-model="form.name" class="mt-1 block w-full"
                            autocomplete="name" placeholder="eg. Michael jackson" />
                        <InputError class="mt-2" :message="form.errors.name" />
                    </div>
                    <div class="">
                        <InputLabel value="Email address*" />
                        <TextInput id="email" type="email" v-model="form.email" class="mt-1 block w-full"
                            autocomplete="email" placeholder="eg. example@address.com" />
                        <InputError class="mt-2" :message="form.errors.email" />
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="">
                        <div class="relative">
                            <div class="absolute bottom-0 top-[60px] right-0 flex items-center pr-3 cursor-pointer">
                                <svg v-if="showPassword" @click="togglePasswordVisibility" width="24" height="24"
                                    viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <g clip-path="url(#clip0_182_11449)">
                                        <path
                                            d="M12 6.5C15.79 6.5 19.17 8.63 20.82 12C19.17 15.37 15.8 17.5 12 17.5C8.2 17.5 4.83 15.37 3.18 12C4.83 8.63 8.21 6.5 12 6.5ZM12 4.5C7 4.5 2.73 7.61 1 12C2.73 16.39 7 19.5 12 19.5C17 19.5 21.27 16.39 23 12C21.27 7.61 17 4.5 12 4.5ZM12 9.5C13.38 9.5 14.5 10.62 14.5 12C14.5 13.38 13.38 14.5 12 14.5C10.62 14.5 9.5 13.38 9.5 12C9.5 10.62 10.62 9.5 12 9.5ZM12 7.5C9.52 7.5 7.5 9.52 7.5 12C7.5 14.48 9.52 16.5 12 16.5C14.48 16.5 16.5 14.48 16.5 12C16.5 9.52 14.48 7.5 12 7.5Z"
                                            fill="#666666" />
                                    </g>
                                    <defs>
                                        <clipPath id="clip0_182_11449">
                                            <rect width="24" height="24" fill="white" />
                                        </clipPath>
                                    </defs>
                                </svg>
                                <svg v-else @click="togglePasswordVisibility" width="24" height="24" viewBox="0 0 24 24"
                                    fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <g clip-path="url(#clip0_182_11448)">
                                        <path
                                            d="M12 6.5C15.79 6.5 19.17 8.63 20.82 12C19.17 15.37 15.8 17.5 12 17.5C8.2 17.5 4.83 15.37 3.18 12C4.83 8.63 8.21 6.5 12 6.5ZM12 4.5C7 4.5 2.73 7.61 1 12C2.73 16.39 7 19.5 12 19.5C17 19.5 21.27 16.39 23 12C21.27 7.61 17 4.5 12 4.5ZM12 9.5C13.38 9.5 14.5 10.62 14.5 12C14.5 13.38 13.38 14.5 12 14.5C10.62 14.5 9.5 13.38 9.5 12C9.5 10.62 10.62 9.5 12 9.5ZM12 7.5C9.52 7.5 7.5 9.52 7.5 12C7.5 14.48 9.52 16.5 12 16.5C14.48 16.5 16.5 14.48 16.5 12C16.5 9.52 14.48 7.5 12 7.5Z"
                                            fill="#666666" />
                                    </g>
                                    <path d="M23 1L0.999999 23" stroke="#666666" stroke-width="2"
                                        stroke-linecap="round" />
                                    <defs>
                                        <clipPath id="clip0_182_11448">
                                            <rect width="24" height="24" fill="white" />
                                        </clipPath>
                                    </defs>
                                </svg>
                            </div>
                            <InputLabel value="Password*" />
                            <TextInput v-model="form.password" :type="showPassword ? 'text' : 'password'" id="password"
                                class=" mt-1 block w-full" autocomplete="password" placeholder="Password" />
                            <InputError class="mt-2" :message="form.errors.password" />
                        </div>
                    </div>
                    <div class="">
                        <div class="relative">
                            <div class="absolute bottom-0 top-[60px] right-0 flex items-center pr-3 cursor-pointer">
                                <svg v-if="showPassword" @click="togglePasswordVisibility" width="24" height="24"
                                    viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <g clip-path="url(#clip0_182_11449)">
                                        <path
                                            d="M12 6.5C15.79 6.5 19.17 8.63 20.82 12C19.17 15.37 15.8 17.5 12 17.5C8.2 17.5 4.83 15.37 3.18 12C4.83 8.63 8.21 6.5 12 6.5ZM12 4.5C7 4.5 2.73 7.61 1 12C2.73 16.39 7 19.5 12 19.5C17 19.5 21.27 16.39 23 12C21.27 7.61 17 4.5 12 4.5ZM12 9.5C13.38 9.5 14.5 10.62 14.5 12C14.5 13.38 13.38 14.5 12 14.5C10.62 14.5 9.5 13.38 9.5 12C9.5 10.62 10.62 9.5 12 9.5ZM12 7.5C9.52 7.5 7.5 9.52 7.5 12C7.5 14.48 9.52 16.5 12 16.5C14.48 16.5 16.5 14.48 16.5 12C16.5 9.52 14.48 7.5 12 7.5Z"
                                            fill="#666666" />
                                    </g>
                                    <defs>
                                        <clipPath id="clip0_182_11449">
                                            <rect width="24" height="24" fill="white" />
                                        </clipPath>
                                    </defs>
                                </svg>
                                <svg v-else @click="togglePasswordVisibility" width="24" height="24" viewBox="0 0 24 24"
                                    fill="none" xmlns="http://www.w3.org/2000/svg">
                                    <g clip-path="url(#clip0_182_11448)">
                                        <path
                                            d="M12 6.5C15.79 6.5 19.17 8.63 20.82 12C19.17 15.37 15.8 17.5 12 17.5C8.2 17.5 4.83 15.37 3.18 12C4.83 8.63 8.21 6.5 12 6.5ZM12 4.5C7 4.5 2.73 7.61 1 12C2.73 16.39 7 19.5 12 19.5C17 19.5 21.27 16.39 23 12C21.27 7.61 17 4.5 12 4.5ZM12 9.5C13.38 9.5 14.5 10.62 14.5 12C14.5 13.38 13.38 14.5 12 14.5C10.62 14.5 9.5 13.38 9.5 12C9.5 10.62 10.62 9.5 12 9.5ZM12 7.5C9.52 7.5 7.5 9.52 7.5 12C7.5 14.48 9.52 16.5 12 16.5C14.48 16.5 16.5 14.48 16.5 12C16.5 9.52 14.48 7.5 12 7.5Z"
                                            fill="#666666" />
                                    </g>
                                    <path d="M23 1L0.999999 23" stroke="#666666" stroke-width="2"
                                        stroke-linecap="round" />
                                    <defs>
                                        <clipPath id="clip0_182_11448">
                                            <rect width="24" height="24" fill="white" />
                                        </clipPath>
                                    </defs>
                                </svg>
                            </div>
                            <InputLabel value="Confirm password*" />
                            <TextInput v-model="form.password_confirmation" :type="showPassword ? 'text' : 'password'"
                                id="password_confirmation" class=" mt-1 block w-full" autocomplete="password"
                                placeholder="Confirm password" />
                            <InputError class="mt-2" :message="form.errors.password_confirmation" />
                        </div>
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="">
                        <InputLabel value="Country*" />
                        <InputSelect :options="countries" placeholder="Choose a country" v-model="form.country_id"
                            @update:model-value="selectedCountry" class="mt-1 block w-full" />
                        <InputError class="mt-2" :message="form.errors.country_id" />
                    </div>
                    <div class="">
                        <InputLabel value="Phone number*" />
                        <TextInput id="phone_number" v-model="form.phone_number" type="text" class="mt-1 block w-full"
                            placeholder="+44 234 345 345" autocomplete="phone_number" />
                        <InputError class="mt-2" :message="form.errors.phone_number" />
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="">
                        <InputLabel value="Billing address*" />
                        <div class="flex gap-3">
                            <TextInput id="street_address" v-model="form.postal_address" type="text"
                                class="mt-1 block w-full" placeholder="Street Address" autocomplete="street_address" />
                            <TextInput id="city" v-model="form.city" type="text" class="mt-1 block !w-2/5"
                                placeholder="City" autocomplete="city" />
                            <TextInput id="state" v-model="form.state" type="text" class="mt-1 block !w-2/5"
                                placeholder="State" autocomplete="state" />
                        </div>
                        <InputError class="mt-2" :message="form.errors.postal_address" />
                    </div>
                    <div class="">
                        <InputLabel value="Status*" />
                        <InputSelect :options="statusList" placeholder="Choose a status" v-model="form.status"
                            class="mt-1 block w-full" />
                        <InputError class="mt-2" :message="form.errors.status" />
                    </div>
                </div>
                <div class="mt-6.5 flex justify-end items-center gap-3">
                    <Link :href="route('client.student.index', { 'client': usePage().props.client.slug })">
                    <ClientSecondaryButton
                        btnClass="whitespace-nowrap gap-3 flex items-center text-primary font-semibold py-2 px-8 border border-primary bg-white rounded-1">
                        Cancel
                    </ClientSecondaryButton>
                    </Link>
                    <ClientPrimaryButton
                        btnClass="whitespace-nowrap gap-3 flex items-center text-white font-semibold py-2 px-8 border border-primary bg-primary rounded-1"
                        :class="{ 'opacity-25': form.processing }" :disabled="form.processing">
                        Create
                    </ClientPrimaryButton>
                </div>
            </template>
        </FormSectionCustom>
    </div>
</template>