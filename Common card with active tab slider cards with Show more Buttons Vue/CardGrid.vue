<script setup>
import { ref, reactive, onMounted, computed } from "vue";
import { Splide, SplideSlide } from "@splidejs/vue-splide";
import "@splidejs/splide/dist/css/themes/splide-default.min.css";
import PrimaryButton from "@/Components/Web/WebRevamp/WebCommoncomponents/PrimaryButton.vue";
import SecondaryButton from "@/Components/Web/WebRevamp/WebCommoncomponents/SecondaryButton.vue";
import CourseCard from "@/Components/Web/WebRevamp/WebCommoncomponents/CourseCard.vue";
import { usePage } from '@inertiajs/vue3'

const categories = [
    {
        name: "Information Technology",
        slides: [
            {
                id: 1,
                title: 'Dummy Course 1',
                subtitle: 'This is a dummy subtitle for IT course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
                cutPrice: '£600',
            },
            {
                id: 2,
                title: 'Dummy Course 2',
                subtitle: 'This is a dummy subtitle for IT course 2',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 3,
                title: 'Dummy Course 3',
                subtitle: 'This is a dummy subtitle for IT course 3',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy IT courses as needed
        ]
    },
    {
        name: "Business",
        slides: [
            {
                id: 1,
                title: 'Dummy Business Course 1',
                subtitle: 'This is a dummy subtitle for Business course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 2,
                title: 'Dummy Business Course 2',
                subtitle: 'This is a dummy subtitle for Business course 2',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 3,
                title: 'Dummy Business Course 3',
                subtitle: 'This is a dummy subtitle for Business course 3',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy Business courses as needed
        ]
    },
    {
        name: "Management",
        slides: [
            {
                id: 1,
                title: 'Dummy Management Course 1',
                subtitle: 'This is a dummy subtitle for Management course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 2,
                title: 'Dummy Management Course 2',
                subtitle: 'This is a dummy subtitle for Management course 2',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy Management courses as needed
        ]
    },
    {
        name: "Administration",
        slides: [
            {
                id: 1,
                title: 'Dummy Admin Course 1',
                subtitle: 'This is a dummy subtitle for Admin course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 2,
                title: 'Dummy Admin Course 2',
                subtitle: 'This is a dummy subtitle for Admin course 2',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy Admin courses as needed
        ]
    },
    {
        name: "Project Management",
        slides: [
            {
                id: 1,
                title: 'Dummy PM Course 1',
                subtitle: 'This is a dummy subtitle for PM course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 2,
                title: 'Dummy PM Course 2',
                subtitle: 'This is a dummy subtitle for PM course 2',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy PM courses as needed
        ]
    },
    {
        name: "HR & Leadership",
        slides: [
            {
                id: 1,
                title: 'Dummy HR Course 1',
                subtitle: 'This is a dummy subtitle for HR course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 2,
                title: 'Dummy Leadership Course 1',
                subtitle: 'This is a dummy subtitle for Leadership course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy HR & Leadership courses as needed
        ]
    },
    {
        name: "Sales & Marketing",
        slides: [
            {
                id: 1,
                title: 'Dummy Sales Course 1',
                subtitle: 'This is a dummy subtitle for Sales course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            {
                id: 2,
                title: 'Dummy Marketing Course 1',
                subtitle: 'This is a dummy subtitle for Marketing course 1',
                image: 'dummy-image-url',
                monthlyPayment: '£100.00',
                fullPayment: '£400',
            },
            // Add more dummy Sales & Marketing courses as needed
        ]
    },
];


const categorySplideRef = ref(null);
const contentSplideRef = ref(null);

const state = reactive({
  hasStarted: false,
  isAtEnd: false,
  activeCategory: categories[0].name,
  progress: 0,
});

const handleCategoryClick = (categoryName) => {
  state.activeCategory = categoryName;
  if (contentSplideRef.value) {
    contentSplideRef.value.go(0);
  }
};

const prevSlide = () => {
  if (categorySplideRef.value) {
    categorySplideRef.value.go("-1");
  }
};

const nextSlide = () => {
  if (categorySplideRef.value) {
    categorySplideRef.value.go("+1");
    state.hasStarted = true;
  }
};

const categorySplideOptions = {
  type: "slide",
  autoWidth: true,
  autoplay: false,
  focus: "left",
  trimSpace: true,
  arrows: false,
  pagination: false,
  gap: "1rem",
  perMove: 1,
  interval: 3000,
  autoScroll: {
    speed: 1,
    pauseOnHover: true,
    pauseOnFocus: false,
  },
};

onMounted(() => {
  const splide = categorySplideRef.value?.splide;
  if (splide) {
    const updateButtons = () => {
      const currentIndex = splide.index;
      const totalSlides = splide.length - splide.options.perPage;
      state.isAtEnd = currentIndex >= totalSlides;
      state.hasStarted = currentIndex > 0;
    };
    splide.on("moved", updateButtons);
    updateButtons();
  }
});

const initialCardCount = ref(6);
const expanded = ref(false);
const sectionRef = ref(null);

const updateInitialCardCount = () => {
    initialCardCount.value = window.innerWidth <= 991 ? 2 : 6;
};

onMounted(() => {
    updateInitialCardCount();
    window.addEventListener('resize', updateInitialCardCount);
});

const activeSlides = computed(() => {
  return categories.find((category) => category.name === state.activeCategory)?.slides || [];
});

const visibleSlides = computed(() => {
  return expanded.value ? activeSlides.value : activeSlides.value.slice(0, initialCardCount.value);
});

const showMoreButton = computed(() => {
  return activeSlides.value.length > initialCardCount.value;
});

function toggleExpand() {
    expanded.value = !expanded.value;
    if (!expanded.value) {
        scrollToSection();
    }
}

function scrollToSection() {
    if (sectionRef.value) {
        const offset = 100;
        const elementPosition = sectionRef.value.getBoundingClientRect().top;
        const offsetPosition = elementPosition + window.pageYOffset - offset;
        
        window.scrollTo({
            top: offsetPosition,
            behavior: "smooth"
        });
    }
}
</script>

<template>
    <section class="bg-ash-1000 py-20 md:py-32 coursecard-section" ref="sectionRef">
        <div class="container">
            <div class="">
                <h1 class="text-xl sm:text-4xl font-bold text-black-500 text-center xl:max-w-[34ch] mx-auto">Master Your Career Growth with Our Top-Rated, Expert-Led Courses</h1>
                <div class="mt-16 md:mt-25">
                    <div class="">
                        <div class="">
                            <div class="">
                                <div class="relative xl:w-3/4 mx-auto">
                                    <button v-if="state.hasStarted" class="prev absolute top-1/2 transform -translate-y-1/2 left-0 z-10" @click.stop="prevSlide">
                                        <i class="fas fa-chevron-left text-white bg-black-900 hover:text-black-900 hover:bg-white border border-black-900 rounded-10 w-[35px] h-[35px] flex justify-center items-center"></i>
                                    </button>
                                    <div class="mx-10 relative">
                                        <Splide :options="categorySplideOptions" ref="categorySplideRef">
                                            <SplideSlide v-for="(category, index) in categories" :key="index">
                                                <div class="my-3 lg:my-5 flex justify-center w-full">
                                                    <div :class="['text-base font-medium rounded-full w-full text-center py-2.5 px-5 border cursor-pointer text-nowrap overflow-hidden',
                                                        state.activeCategory === category.name
                                                            ? 'text-black-900 bg-green-200 border-indigo-200'
                                                            : 'text-black-900 bg-white border-indigo-200',
                                                        ]"
                                                        @click="handleCategoryClick(category.name)"
                                                    >
                                                        {{ category.name }}
                                                    </div>
                                                </div>
                                            </SplideSlide>
                                        </Splide>
                                    </div>
                                    <button v-if="!state.isAtEnd" class="next absolute top-1/2 transform -translate-y-1/2 right-0 z-10" @click.stop="nextSlide">
                                        <i class="fas fa-chevron-right text-white bg-black-900 hover:text-black-900 hover:bg-white border border-black-900 rounded-10 w-[35px] h-[35px] flex justify-center items-center"></i>
                                    </button>
                                </div>
                            </div>
                            <div class="col-span-1 lg:col-span-1 border-bottom"></div>
                        </div>
                        <!-- Content slider -->
                        <div class="">
                            <div class="">
                                <div class="py-10 px-4">
                                    <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-3 gap-6 py-10">
                                        <transition-group name="card-list">
                                            <CourseCard
                                                v-for="card in visibleSlides"
                                                :key="card.id"
                                                :card="card"
                                            />
                                        </transition-group>
                                    </div>
                                    <div class="mt-12 flex justify-center items-center gap-4">
                                        <PrimaryButton v-if="showMoreButton" @click="toggleExpand" class="whitespace-nowrap gap-3 flex items-center text-white font-bold py-2.5 px-4 border border-black-800 bg-black-800 rounded-2 text-lg">
                                            {{ expanded ? 'Show less' : 'Show more' }}
                                        </PrimaryButton>
                                        <SecondaryButton>
                                            View all
                                        </SecondaryButton>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<style scoped>
    .coursecard-section{
        -webkit-clip-path: polygon(0 0,100% 5.2vw,100% calc(100% - 3.2vw),0 100%);
        clip-path: polygon(0 0,100% 5.2vw,100% calc(100% - 3.2vw),0 100%);
    }

    .card-list-enter-active,
    .card-list-leave-active {
        transition: opacity 0.5s ease, transform 0.5s ease;
    }

    .card-list-enter-from,
    .card-list-leave-to {
        opacity: 0;
        transform: translateY(30px);
    }
</style>