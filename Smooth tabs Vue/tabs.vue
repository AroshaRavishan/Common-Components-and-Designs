<script setup>
import { ref } from 'vue';
import Branding from './MyProfileComponents/BrandingIndex.vue';
import BusinessDetails from './MyProfileComponents/BusinessDetailsIndex.vue';
import CertificateTemplates from './MyProfileComponents/CertificateTemplatesIndex.vue';
import Localization from './MyProfileComponents/LocalizationIndex.vue';
import MainDetails from './MyProfileComponents/MainDetailsIndex.vue';

const props = defineProps({
    activeTab: {
        type: String,
        required: true
    },
})
 
const openTab = ref(props.activeTab? parseInt(props.activeTab) : 1 );
const toggleTabs = (tabNumber) => {
  openTab.value = tabNumber
}

</script>
 
<template>
    <div class="main-wrapper">
        <div class="mt-8">
            <div class="flex flex-wrap">
                <div class="w-full">
                    <ul class="flex mb-0 list-none flex-wrap pt-3 pb-4 flex-row border-b border-ash-750 gap-10">
                        <li class="-mb-px mr-2 last:mr-0 text-center cursor-pointer">
                            <a class="text-base px-5 py-4" v-on:click="toggleTabs(1)" v-bind:class="{'text-ash-750 font-normal': openTab !== 1, 'text-primary border-b-[3px] border-primary font-medium': openTab === 1}">
                                Main Details
                            </a>
                        </li>
                        <li class="-mb-px mr-2 last:mr-0 text-center cursor-pointer">
                            <a class="text-base px-5 py-4" v-on:click="toggleTabs(2)" v-bind:class="{'text-ash-750 font-normal': openTab !== 2, 'text-primary border-b-[3px] border-primary font-medium': openTab === 2}">
                                Business Details
                            </a>
                        </li>
                        <li class="-mb-px mr-2 last:mr-0 text-center cursor-pointer">
                            <a class="text-base px-5 py-4" v-on:click="toggleTabs(3)" v-bind:class="{'text-ash-750 font-normal': openTab !== 3, 'text-primary border-b-[3px] border-primary font-medium': openTab === 3}">
                                Branding
                            </a>
                        </li>
                        <li class="-mb-px mr-2 last:mr-0 text-center cursor-pointer">
                            <a class="text-base px-5 py-4" v-on:click="toggleTabs(4)" v-bind:class="{'text-ash-750 font-normal': openTab !== 4, 'text-primary border-b-[3px] border-primary font-medium': openTab === 4}">
                                Localization Details
                            </a>
                        </li>
                        <li class="-mb-px mr-2 last:mr-0 text-center cursor-pointer">
                            <a class="text-base px-5 py-4" v-on:click="toggleTabs(5)" v-bind:class="{'text-ash-750 font-normal': openTab !== 5, 'text-primary border-b-[3px] border-primary font-medium': openTab === 5}">
                                Certificate Templates
                            </a>
                        </li>
                    </ul>
                    <div class="relative flex flex-col min-w-0 break-words  w-full my-6">
                        <div class="flex-auto">
                            <div class="tab-content tab-space">
                                <div v-bind:class="{'hidden': openTab !== 1, 'block': openTab === 1}">
                                    <MainDetails />
                                </div>
                                <div v-bind:class="{'hidden': openTab !== 2, 'block': openTab === 2}">
                                    <BusinessDetails/>
                                </div>
                                <div v-bind:class="{'hidden': openTab !== 3, 'block': openTab === 3}">
                                    <Branding/>
                                </div>
                                <div v-bind:class="{'hidden': openTab !== 4, 'block': openTab === 4}">
                                   <Localization :currencies="currencies"/>
                                </div>
                                <div v-bind:class="{'hidden': openTab !== 5, 'block': openTab === 5}">
                                   <CertificateTemplates :certificates="certificates" />
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
       
    </div>
</template>
 
 
<style scoped>
 
</style>