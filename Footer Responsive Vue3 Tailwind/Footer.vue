<script setup>
import {
    ref,
    defineProps,
    onMounted,
    watch
} from "vue";
import {
    Link,
    usePage
} from "@inertiajs/vue3";

const fullYear = ref(new Date().getFullYear() + "");

defineProps({
    removemargin: {
        type: String,
        default: null,
    },
});

const selectedCurrency = ref(usePage().props.currencyCodes.currencyCode);

onMounted(() => {
    localStorage.setItem('selectedCurrency', selectedCurrency.value);
});

watch(selectedCurrency, (newValue) => {
    localStorage.setItem('selectedCurrency', newValue);
});

const localStorageCurrency = localStorage.getItem('selectedCurrency');
if (localStorageCurrency) {
    selectedCurrency.value = localStorageCurrency;
}

const updateLocalStorage = () => {
    localStorage.setItem('selectedCurrency', selectedCurrency.value);
    window.location.reload()
};

const languages = ['English', 'Spanish', 'French', 'German', 'Italian']
const selectedLanguage = ref('')
const isOpen = ref(false)

const toggleDropdown = () => {
    isOpen.value = !isOpen.value
}

const selectLanguage = (language) => {
    selectedLanguage.value = language
    isOpen.value = false
}

const applyLanguage = () => {

}
</script>

<template>
    <div class="w-full h-full bg-beige-100 footer" :class="removemargin ? '' : 'mt-10 md:mt-30'">
        <div class="container pt-16 pb-9">
            <div class="grid gap-16 row-gap-10 lg:grid-cols-6">
                <div class="md:max-w-full lg:col-span-2">
                    <a href="/" class="flex justify-center lg:inline-flex items-center">
                        <img loading="lazy" alt="GelLogo" class="" src="https://i.imghippo.com/files/LzYzY1720858499.png">
                    </a>
                    <div class="mt-7">
                        <h3 class="text-sm font-normal text-black-900">Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. </h3>
                        <div class="mt-6">
                            <div class="flex justify-center lg:justify-start">
                                <div class="social-buttons flex flex-wrap gap-1">
                                    <a href="#" class="social-button facebook w-[50px] h-[50px] xl:w-[60px] xl:h-[60px] rounded-full bg-beige-200 flex justify-center items-center relative hover:text-white transform transition duration-1000 hover:scale-105" aria-label="Facebook">
                                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/FacebookLogo.svg' : '../../web-assets/FacebookLogo.svg'" alt="FacebookLogo" class="">
                                    </a>
                                    <a href="#" class="social-button instagram w-[50px] h-[50px] xl:w-[60px] xl:h-[60px] rounded-full bg-beige-200 flex justify-center items-center relative hover:text-white transform transition duration-1000 hover:scale-105" aria-label="Instagram">
                                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/InstagramLogo.svg' : '../../web-assets/InstagramLogo.svg'" alt="InstagramLogo" class="">
                                    </a>
                                    <a href="#" class="social-button twitter w-[50px] h-[50px] xl:w-[60px] xl:h-[60px] rounded-full bg-beige-200 flex justify-center items-center relative hover:text-white transform transition duration-1000 hover:scale-105" aria-label="Twitter">
                                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/TwitterXLogo.svg' : '../../web-assets/TwitterXLogo.svg'" alt="TwitterXLogo" class="">
                                    </a>
                                    <a href="#" class="social-button linkedin w-[50px] h-[50px] xl:w-[60px] xl:h-[60px] rounded-full bg-beige-200 flex justify-center items-center relative hover:text-white transform transition duration-1000 hover:scale-105" aria-label="LinkedIn">
                                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/LinkedInLogo.svg' : '../../web-assets/LinkedInLogo.svg'" alt="LinkedInLogo" class="">
                                    </a>
                                    <a href="#" class="social-button youtube w-[50px] h-[50px] xl:w-[60px] xl:h-[60px] rounded-full bg-beige-200 flex justify-center items-center relative hover:text-white transform transition duration-1000 hover:scale-105" aria-label="YouTube">
                                        <img loading="lazy" :src="$page.props.assetURL ? $page.props.assetURL + '/web-assets/YouTubeLogo.svg' : '../../web-assets/YouTubeLogo.svg'" alt="YouTubeLogo" class="">
                                    </a>
                                </div>
                            </div>
                        </div>
                        <div class="text-center lg:text-left">
                            <a href="#"><button type="button" class="text-center text-lg text-white font-bold bg-green-100 rounded-lg w-full mt-9 py-2.5">
                                    Verify Your Certificate
                                </button></a>
                        </div>
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-5 row-gap-8 lg:col-span-4 md:grid-cols-4">
                    <div>
                        <div class="font-semibold text-base text-ash-1300">Quick Links</div>
                        <ul class="mt-7 space-y-2.5">
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 1
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 2
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 3
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 4
                                </Link>
                            </li>
                            <li>
                                <div class="flex mt-4">
                                    <select v-model="selectedCurrency" @change="updateLocalStorage" class="p-2 border border-gray-300 rounded">
                                        <option value="GBP">GBP</option>
                                        <option value="CAD">CAD</option>
                                        <option value="USD">USD</option>
                                        <option value="EURO">EURO</option>
                                        <option value="INR">INR</option>
                                        <option value="AED">AED</option>
                                    </select>
                                </div>
                            </li>
                        </ul>
                    </div>
                    <div>
                        <div class="font-semibold text-base text-ash-1300">Resources</div>
                        <ul class="mt-7 space-y-2.5">
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 5
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 6
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 7
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 8
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 9
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 10
                                </Link>
                            </li>
                        </ul>
                    </div>
                    <div>
                        <div class="font-semibold text-base text-ash-1300">Resources</div>
                        <ul class="mt-7 space-y-2.5">
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 11
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 12
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 13
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 14
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 15
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300

" href="#">
                                Sample Link 16
                                </Link>
                            </li>
                        </ul>
                    </div>
                    <div>
                        <div class="font-semibold text-base text-ash-1300">More Resources</div>
                        <ul class="mt-7 space-y-2.5">
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 17
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 18
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 19
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 20
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 21
                                </Link>
                            </li>
                            <li>
                                <Link class="font-normal text-sm text-ash-1300" href="#">
                                Sample Link 22
                                </Link>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
            <div class="flex flex-col lg:flex-row justify-between items-center pt-5 pb-10">
                <p class="text-sm text-ash-1300 text-center">© Arosha Ravishan <span>{{ fullYear }}</span>. All rights reserved.</p>
                <ul class="flex flex-wrap gap-3 justify-center mt-2 lg:mt-0">
                    <li>
                        <Link href="#" class="font-normal text-sm text-ash-1300">Privacy Policy</Link>
                    </li>
                    <li>
                        <Link href="#" class="font-normal text-sm text-ash-1300">Terms of Service</Link>
                    </li>
                    <li>
                        <Link href="#" class="font-normal text-sm text-ash-1300">Cookie Policy</Link>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>