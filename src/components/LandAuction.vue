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
            :lands="filterLandBaseOnAction()"
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
            lands: [
                {
                    id: 1,
                    name: 'Land 1',
                    region: 0,
                    level: 1,
                    isForSale: false,
                    price: 0,
                    owner: {
                        name: 'User 1',
                        walletAddress: '0x000000000000000000000000000000000001',
                    }
                },
                {
                    id: 2,
                    name: 'Land 2',
                    region: 0,
                    level: 1,
                    isForSale: false,
                    price: 0,
                    owner: {
                        name: 'User 2',
                        walletAddress: '0x000000000000000000000000000000000002',
                    }
                },
                {
                    id: 3,
                    name: 'Land 3',
                    region: 1,
                    level: 1,
                    isForSale: true,
                    price: 300000,
                    owner: {
                        name: 'User 3',
                        walletAddress: '0x000000000000000000000000000000000003',
                    }
                },
                {
                    id: 4,
                    name: 'Land 4',
                    region: 1,
                    level: 1,
                    isForSale: true,
                    price: 400000,
                    owner: {
                        name: 'User 4',
                        walletAddress: '0x000000000000000000000000000000000004',
                    }
                },
                {
                    id: 5,
                    name: 'Land 5',
                    region: 2,
                    level: 1,
                    isForSale: false,
                    price: 0,
                    owner: {
                        name: 'User 5',
                        walletAddress: '0x000000000000000000000000000000000005',
                    }
                },
            ]
        }
    },

    methods: {
        toggle() {
            this.isOpen = !this.isOpen;
        },

        filterLandBaseOnAction() {
            if (this.action === 0) return this.lands

            return this.lands.filter(land => land.isForSale)
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
    margin: 0;
    padding: 60px 3% 30px;
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
        margin-top: 0;
        padding-top: 30px;
        overflow-x: hidden;
    }
}
</style>