<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from 'vue';

defineProps({
  images: {
    type: Array as () => string[],
    required: true,
  },
  columns: {
    type: Number,
    default: 3,
  },
  borderWidth: {
    type: String,
    default: '0',
  },
  animationDuration: {
    type: Number,
    default: 48,
  },
  perspective: {
    type: Boolean,
    default: false,
  },
});

const isometricImageFlow = ref<HTMLElement | null>(null);
const scale = ref(2);

let resizeObserver: ResizeObserver | null = null;

onMounted(() => {
  if (!isometricImageFlow.value) {
    return;
  }
  resizeObserver = new ResizeObserver(() => {
    const width = isometricImageFlow.value?.clientWidth || 0;
    const height = isometricImageFlow.value?.clientHeight || 0;
    const ratio = height > 0 ? width / height : 1;
    scale.value = ratio > 1.2 ? 2 : 2.4 / ratio;
  });
  resizeObserver.observe(isometricImageFlow.value);
});

onBeforeUnmount(() => {
  if (resizeObserver) {
    resizeObserver.disconnect();
  }
});
</script>
<template>
  <div
    ref="isometricImageFlow"
    class="isometric-image-flow"
    :class="{ perspective }"
    :style="{
      '--image-border-width': borderWidth || '0',
      '--animation-duration': `${animationDuration}s`,
    }"
  >
    <div
      class="isometric-image-flow__perspective"
      :style="{
        transform: perspective
          ? `rotateX(60deg) rotateY(-15deg) rotateZ(30deg) translateX(-20%) scale(${scale})`
          : `rotateX(60deg) rotateY(-15deg) rotateZ(30deg) scale(${scale})`,
      }"
    >
      <div class="isometric-image-flow__box">
        <div
          class="isometric-image-flow__part"
          v-for="column in [...Array(2).keys()]"
        >
          <ul
            class="isometric-image-flow__column"
            v-for="column in [...Array(columns).keys()]"
            :key="column"
          >
            <li
              class="isometric-image-flow__image"
              v-for="(image, index) in images.filter(
                (_, i) => i % columns === column,
              )"
              :key="index"
            >
              <img :src="image" alt="Image" loading="lazy" />
            </li>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>
<style lang="css" scoped>
.isometric-image-flow {
  position: relative;
  overflow: hidden;
  &::after {
    content: '';
    pointer-events: none;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(
      -30deg,
      rgba(235, 167, 0, 0.25) 0%,
      rgba(0, 0, 0, 0) 100%
    );
    backdrop-filter: saturate(60%) blur(4px);
  }
}
.isometric-image-flow__perspective {
  transform-style: preserve-3d;
  width: 100%;
  height: 100%;
  transform: rotateX(60deg) rotateY(-15deg) rotateZ(30deg) scale(2);
}
.isometric-image-flow.perspective {
  perspective: 4800px;
  .isometric-image-flow__perspective {
    transform: rotateX(60deg) rotateY(-15deg) rotateZ(30deg) translateX(-20%)
      scale(2);
  }
}
.isometric-image-flow__box {
  display: flex;
  flex-direction: column;
  gap: 1em;
  animation: flowing 36s infinite linear;
  animation-duration: var(--animation-duration);
}
@keyframes flowing {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(calc(-50% - 0.5em));
  }
}
.isometric-image-flow__part {
  display: flex;
  gap: 1em;
}
.isometric-image-flow__column {
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 1em;
}
.isometric-image-flow__image {
  list-style: none;
  flex-grow: 1;
  border: 0.5em solid #fff;
  border-width: var(--image-border-width);
  > img {
    display: block;
    width: 100%;
    height: 100%;
    min-width: 10px;
    min-height: 10px;
    object-fit: cover;
  }
}
</style>
