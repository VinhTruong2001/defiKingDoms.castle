<template>
    <div class="land-list game-scroll-bar row">
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
</style>