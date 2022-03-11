<template>
    <div
        :class="`land-auction overlay ${this.isOpen ? 'active' : ''}`"
    >
        <!-- Filter -->
        <land-filter />

        <!-- Land display -->
        <div class="land-view game-border fancy">
            <div
                class="close-btn click-cursor"
                @click="this.toggle()"
            ></div>
        </div>
    </div>
</template>

<script>
import LandFilter from './LandFilter.vue';

export default {
  components: { LandFilter },
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

.land-view {
    flex: 0.75;
    height: 100%;
}

@media (max-width: 376px) {
    .land-auction {
        flex-direction: column;
    }

    .filter {
        flex: 1;
        height: unset;
        margin: 0;
    }

    .land-view {
        flex: 1;
        height: unset;
    }
}
</style>