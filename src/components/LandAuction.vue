<template>
    <div
        :class="`land-auction overlay row ${isOpen ? 'active' : ''}`"
    >
        <!-- Filter -->
        <land-filter />

        <!-- Land display -->
        <land-view
            :closeLandAuction="() => toggle()"
            :action="action"
            :lands="[]"
        />
    </div>
</template>

<script>
import LandFilter from './LandFilter.vue';
import LandView from './LandView.vue';


export default {
    props: ['action'],

    components: {
      LandFilter,
      LandView,
    },

    data() {
        return {
            isOpen: false,
        }
    },

    methods: {
        toggle() {
            this.isOpen = !this.isOpen;
        }
    }
}
</script>

<style scoped>
.land-auction {
    z-index: -1;
    opacity: 0;
    will-change: opacity;
    transition: all 0.5s linear;
    margin: 60px 0 30px;
    padding: 0 3%;
    box-sizing: border-box;
}

.land-auction.active {
    z-index: 3000;
    opacity: 1;
    will-change: opacity;
    transition: all 0.5s linear;
}

@media (max-width: 1024px) {
    .land-auction {
        margin-bottom: 0;
        align-items: unset;
    }
}
</style>