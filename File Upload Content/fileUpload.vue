<!-- Help Content -->
<script setup>
import { ref } from 'vue';

const fileInput = ref(null);
const fileName = ref('');
const progress = ref(0);
const showVerifyIcon = ref(false);

const handleDrop = (event) => {
    const files = event.dataTransfer.files;
    handleFile(files[0]);
};

const handleFileChange = (event) => {
    const files = event.target.files;
    handleFile(files[0]);
};

const handleFile = (file) => {
    if (!file) return;

    if (file.size > 10 * 1024 * 1024) {
        alert('File size exceeds 10MB');
        return;
    }

    fileName.value = file.name;
    uploadFile(file);
};

const uploadFile = (file) => {
    const formData = new FormData();
    formData.append('file', file);

    const xhr = new XMLHttpRequest();
    xhr.open('POST', 'YOUR_UPLOAD_URL');

    xhr.upload.onprogress = (event) => {
        if (event.lengthComputable) {
            progress.value = Math.round((event.loaded / event.total) * 100);
        }
    };

    xhr.onload = () => {
        if (xhr.status === 200) {
            showVerifyIcon.value = true;
        } else {
            alert('Upload failed');
        }
        progress.value = 0;
    };

    xhr.onerror = () => {
        alert('Upload failed');
        progress.value = 0;
    };

    xhr.send(formData);
};

</script>
<template>
    <div class="mt-5">
        <div class="mt-7">
            <div class="">
                <InputLabel value="Attachments" />
                <div class="flex items-center justify-center w-full py-10 relative">
                    <label for="dropzone-file"
                        class="flex flex-col items-center justify-center w-full h-auto border border-dashed border-primary rounded-lg cursor-pointer bg-gray-50 dark:hover:bg-bray-800 dark:bg-gray-700 hover:bg-gray-100 dark:border-gray-600 dark:hover:border-gray-500 dark:hover:bg-gray-600"
                        @dragover.prevent @drop.prevent="handleDrop">
                        <div class="flex flex-col items-center justify-center pt-5 pb-6">
                            <svg class="w-8 h-8 mb-4 text-primary dark:text-gray-400" aria-hidden="true"
                                xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 20 16">
                                <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round"
                                    stroke-width="2"
                                    d="M13 13h3a3 3 0 0 0 0-6h-.025A5.56 5.56 0 0 0 16 6.5 5.5 5.5 0 0 0 5.207 5.021C5.137 5.017 5.071 5 5 5a4 4 0 0 0 0 8h2.167M10 15V6m0 0L8 8m2-2 2 2" />
                            </svg>
                            <p class="mb-2 text-base text-black-700 dark:text-gray-400 font-medium">
                                <span class="font-semibold">Click to upload</span> or drag and drop
                            </p>
                            <p class="text-sm text-black-700 dark:text-gray-400">
                                DOC, DOCX, PDF, TXT, PPT, PPTX, XLS, XLSX, ZIP, RAR, JPG, PNG, JPEG
                            </p>
                            <p class="text-sm text-black-700 dark:text-gray-400">
                                (MAX 10MB)
                            </p>
                            <p class="text-sm text-red-600">
                                If you have multiple files, please zip them and upload
                            </p>
                            <p v-if="fileName"
                                class="text-base md:text-lg font-normal text-green-500 dark:text-green-400 text-center">
                                {{ fileName }}
                            </p>
                        </div>
                        <input id="dropzone-file" type="file" class="hidden" ref="fileInput"
                            @change="handleFileChange" />

                        <div v-if="progress > 0 && progress < 100" class="mt-2">
                            <div class="relative pt-1">
                                <div class="flex mb-2 items-center justify-between">
                                    <div>
                                        <span
                                            class="text-xs font-semibold inline-block py-1 px-2 uppercase rounded-full text-teal-600 bg-teal-200">
                                            In Progress
                                        </span>
                                    </div>
                                    <div class="text-right">
                                        <span class="text-xs font-semibold inline-block text-teal-600">
                                            {{ progress }}%
                                        </span>
                                    </div>
                                </div>
                                <div class="flex flex-col mb-2">
                                    <div class="flex w-full items-center">
                                        <div class="w-full bg-gray-200 rounded-full">
                                            <div :style="{ width: progress + '%' }"
                                                class="text-center text-white bg-teal-500 rounded-full">
                                                <!-- Progress bar content -->
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <div v-if="showVerifyIcon" class="mt-2 flex gap-3 items-center">
                            <p class="text-base md:text-lg font-normal text-green-500 dark:text-green-400 text-center">
                                Successfully submitted
                            </p>
                            <svg class="w-5 h-5 text-green-500 dark:text-green-400" aria-hidden="true"
                                xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                stroke="currentColor">
                                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                                    d="M5 13l4 4L19 7" />
                            </svg>
                        </div>
                    </label>
                </div>
            </div>

        </div>
    </div>
</template>