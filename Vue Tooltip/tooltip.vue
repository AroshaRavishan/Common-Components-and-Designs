<template>
  <button
    @mouseover="showTooltip = true"
    @mouseleave="showTooltip = false"
    @click="toggleTooltip"
    class="tooltip-btn"
  >
    <div v-html="icon"></div>
    <transition name="fade">
      <div v-if="showTooltip" class="tooltip">
        <div class="tooltip-content">{{ content }}</div>
        <div class="tooltip-arrow"></div>
      </div>
    </transition>
  </button>
</template>
    
    <script setup>
import { ref, defineProps } from "vue";

const props = defineProps({
  content: String,
  icon: String,
});

const showTooltip = ref(false);

const toggleTooltip = () => {
  showTooltip.value = !showTooltip.value;
};
</script>
    
    <style scoped>
.tooltip {
  position: absolute;
  z-index: 1;
  background-color: #333;
  color: #fff;
  padding: 5px 15px;
  border-radius: 5px;
  opacity: 1;
  transform: translate(-5%,-100%);
  transition: opacity .3s ease,transform .3s ease;
  bottom: 5px;
  font-weight: 500;
  width: max-content;
  font-size: 14px;
}

.tooltip-btn {
  position: relative;
  border: none;
  border-radius: 6px;
  width: auto;
  height: auto;
  display: flex;
  justify-content: center;
  align-items: center;
}

/* .tooltip-btn:hover {
  border: 1px solid #8d1cba;
} */

.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-left: 5px solid transparent;
  border-right: 5px solid transparent;
  border-bottom: 5px solid #333;
  bottom: 0px;
  left: 50%;
  transform: translateX(-50%);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
  transform: translate(-5%, -120%);
}

.more-icon .tooltip-btn {
  border: none !important;
}

.more-icon .tooltip {
  right: 0;
}
</style>