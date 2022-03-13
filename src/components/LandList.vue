<template>
    <div class="land-list game-scroll-bar row" v-if="lands.length !== 0">
        <div
            class="col c-12 l-3"
            v-for="land in lands"
            :key="land.id"
        >
            <land-item
                :land="land"
                :action="action"
            />
        </div>
    </div>

    <div class="land-list--empty" v-if="lands.length === 0">
        <p>No lands available in this category.</p>
    </div>
</template>

<script>
import LandItem from './LandItem.vue'

export default {
    components: {
        LandItem
    },

    props: [
        'lands',
        'action'
    ],
}
</script>

<style scoped>
.land-list {
    flex: 1;
    overflow-y: auto;
    position: relative;
    z-index: 1;
    margin-top: 20px;
}

.land-list--empty p {
    margin-top: 16px;
    font-size: 14px;
    text-align: center;
    color: #3e1f05;
}
</style>