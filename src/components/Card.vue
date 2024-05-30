<template>
<div
    class="card"
>
    <div
    class="card__inner"
    :class="{ 'is-flipped': isFlipped }"
    @click="onToggleFlipCard"
    >
    <div class="card__face card__face--front">
        <div
        class="card__content"
        ></div>
    </div>
    <div class="card__face card__face--back">
        <div
        class="card__content"
        :style="{ backgroundImage }"
        ></div>
    </div>
    </div>
</div>
</template>

<script setup>
    import { ref, defineProps } from 'vue'

    const props = defineProps({
      imgBackFaceUrl: {
        type: String,
        required: true,
      }
    })

    const imageUrl = require('@/assets/' + props.imgBackFaceUrl);
    const a = {
      backgroundImage: `url(${imageUrl})`,
    }
    
    const isFlipped = ref(false);

    function onToggleFlipCard() {
        isFlipped.value = !isFlipped.value;
    }
</script>

<style lang="css" scoped>
.card {
  display: inline-block;
  margin-right: 1rem;
  margin-bottom: 1rem;
  width: 90px;
  height: 120px;
}

.card__inner {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}

.card.disabled .card__inner {
  cursor: default;
}

.card__inner.is-flipped {
  transform: rotateY(-180deg);
}

.card__face {
  position: absolute;
  width: 100%;
  height: 100%;
  backface-visibility: hidden;
  overflow: hidden;
  border-radius: 1rem;
  padding: 1rem;
  box-shadow: 0 3px 18px 3px rgba(0, 0, 0, 0.2);
}

.card__face--front .card__content {
  background: url("../assets/images/icon_back.png") no-repeat center center;
  background-size: 40px;
  height: 100%;
  width: 100%;
}

.card__face--back {
  background-color: var(--light);
  transform: rotateY(-180deg);
}

.card__face--back .card__content {
  background-position: center center;
  background-repeat: no-repeat;
  background-size: contain;
  height: 100%;
  width: 100%;
}
</style>
