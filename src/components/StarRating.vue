<script setup lang="ts">
import { computed } from "vue"
const props = withDefaults(defineProps<{
    rating: number,
    maxStars?: number,
    size?: string,
    color?: string,
}>(), {
    rating: 5,
    maxStars: 5,
    size: "2rem",
    color: "#F9B316",
});
const values = computed(() => {
    const ratings = Math.round(props.rating * 2) / 2;
    const fullStars = Math.floor(ratings);
    const halfStars = ratings - (Math.floor(ratings)) > 0 ? 1 : 0;
    const emptyStars = props.maxStars - fullStars - halfStars;
    return { ratings, fullStars, halfStars, emptyStars };
});
</script>

<template>
    <div style="display: flex;">
        <!-- full -->
        <svg v-for="_ in values.fullStars" viewBox="0 0 24 24" :width="props.size" :height="props.size">
            <path :fill="props.color"
                d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z" />
        </svg>
        <!-- half -->
        <svg v-for="_ in values.halfStars" viewBox="0 0 24 24" :width="props.size" :height="props.size">
            <path :fill="props.color"
                d="M22,9.24l-7.19-0.62L12,2L9.19,8.63L2,9.24l5.46,4.73L5.82,21L12,17.27L18.18,21l-1.63-7.03L22,9.24z M12,15.4V6.1 l1.71,4.04l4.38,0.38l-3.32,2.88l1,4.28L12,15.4z" />
        </svg>
        <!-- empty -->
        <svg v-for="_ in values.emptyStars" viewBox="0 0 24 24" :width="props.size" :height="props.size">
            <path :fill="props.color"
                d="M22 9.24l-7.19-.62L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21 12 17.27 18.18 21l-1.63-7.03L22 9.24zM12 15.4l-3.76 2.27 1-4.28-3.32-2.88 4.38-.38L12 6.1l1.71 4.04 4.38.38-3.32 2.88 1 4.28L12 15.4z" />
        </svg>
    </div>
</template>