<template>
    <div class="mt-10 md:mt-30 bg-white">
        <div class="container">
            <div class="flex justify-between items-center">
                <button @click="toggleDrawer" aria-controls="drawer-example"
                    class="whitespace-nowrap text-center text-sm text-white font-semibold bg-purple-200 border border-primary rounded-full px-5 py-2 my-5"
                    tabindex="0" type="button"><span class="flex gap-3 items-center">Filters (4)<span
                            class="cds-button-endIcon"><svg aria-hidden="true" fill="none" focusable="false" height="16"
                                viewBox="0 0 16 16" width="16" id="cds-react-aria-286" class="css-0">
                                <path fill-rule="evenodd" clip-rule="evenodd"
                                    d="M12.5 11.5a1 1 0 100 2 1 1 0 000-2zm-2 1a2 2 0 114 0 2 2 0 01-4 0z"
                                    fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd"
                                    d="M11 13H2v-1h9v1zM12.5 2.5a1 1 0 100 2 1 1 0 000-2zm-2 1a2 2 0 114 0 2 2 0 01-4 0z"
                                    fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd"
                                    d="M11 4H2V3h9v1zM5 8.5H2v-1h3v1zM14 8.5H8v-1h6v1z" fill="currentColor"></path>
                                <path fill-rule="evenodd" clip-rule="evenodd"
                                    d="M6.5 7a1 1 0 100 2 1 1 0 000-2zm-2 1a2 2 0 114 0 2 2 0 01-4 0z"
                                    fill="currentColor"></path>
                            </svg></span></span>
                </button>

                <button @click="rotateSVG" id="dropdownInformationButton" data-dropdown-toggle="dropdownInformation"
                    class="whitespace-nowrap text-black-900 text-base font-normal px-5 py-2.5 text-center inline-flex items-center"
                    type="button">
                    <span class="font-semibold text-black-700">Sort by: </span>Best Match
                    <svg :class="{ 'rotated': isRotated }" class="w-2.5 h-2.5 ms-3" aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 10 6">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="m1 1 4 4 4-4" />
                    </svg>
                </button>

                <!-- Dropdown menu -->
                <div id="dropdownInformation" class="z-10 hidden bg-white border border-primary rounded-lg shadow w-48">
                    <ul class="py-2 text-sm text-gray-700 dark:text-gray-200 p-3"
                        aria-labelledby="dropdownInformationButton">
                        <li>
                            <div href="#"
                                class="block px-4 py-2 hover:bg-purple-100 dark:hover:bg-gray-600 dark:hover:text-white rounded-3 hover:rounded-3">
                                Newest</div>
                        </li>
                        <li>
                            <div href="#"
                                class="block px-4 py-2 hover:bg-purple-100 dark:hover:bg-gray-600 dark:hover:text-white  rounded-3 hover:rounded-3">
                                Trending</div>
                        </li>
                        <li>
                            <div href="#"
                                class="block px-4 py-2 hover:bg-purple-100 dark:hover:bg-gray-600 dark:hover:text-white  rounded-3 hover:rounded-3">
                                Free</div>
                        </li>
                    </ul>
                </div>

            </div>

            <!-- drawer component -->
            <div>
                <div v-if="showDrawer" class="overlay" @click="closeDrawer"></div>
                <div class="drawer" :class="{ 'smooth': showDrawer }">
                    <h5 id="drawer-right-label" class="text-primary font-semibold text-lg mt-3">
                        Filter by
                    </h5>
                    <button @click="closeDrawer" type="button" class="close-button">
                        <svg class="w-3 h-3" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                            viewBox="0 0 14 14">
                            <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6" />
                        </svg>
                        <span class="sr-only">Close menu</span>
                    </button>
                    <!-- Content inside the drawer -->
                    <p>This is some content inside the drawer.</p>
                </div>
            </div>

        </div>
    </div>
</template>

<script setup>
import {
    ref
} from 'vue';

const showDrawer = ref(false);

const toggleDrawer = () => {
    showDrawer.value = !showDrawer.value;
};

const closeDrawer = () => {
    showDrawer.value = false;
};

const isRotated = ref(false);

const rotateSVG = () => {
    isRotated.value = !isRotated.value;
};
</script>

<style scoped>
.overlay {
    position: fixed;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.5);
    z-index: 100;
    transition: opacity 0.5s ease;
}

.drawer {
    position: fixed;
    top: 0;
    left: 0;
    bottom: 0;
    width: 100%;
    /* Adjust width as needed */
    background-color: white;
    z-index: 101;
    transform: translateX(-100%);
    transition: transform 0.6s ease;
}

.drawer.smooth {
    transform: translateX(0);
}

.close-button {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    cursor: pointer;
}

.rotated {
    transform: rotate(180deg);
}
</style>