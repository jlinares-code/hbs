<template>
    <section class="animate__animated animate__zoomIn">
        <h2>Segunda parte</h2>
        <div class="pack">
            <GiftCard v-for="(regalo, i) in regalos" :key="i" :item="regalo" />
        </div>
    </section>
</template>

<script>
import GiftCard from './GiftCard.vue'
export default {
    components: { GiftCard },
    props: ['regalos']
}
</script>

<style scoped>
.pack {
    display: flex;
    gap: 1rem;
    justify-content: center;
    flex-wrap: wrap;
    margin-top: 1.5rem;
}

img {
    width: 120px;
    border-radius: 10px;
    box-shadow: 0 0 5px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s;
    cursor: pointer;
}

img:hover {
    transform: scale(1.05);
}
</style>