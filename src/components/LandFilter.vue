<template>
    <div class="filter game-border basic">
        <template v-if="isExpanded">
            <!-- Header -->
            <div class="filter-header">
                <div class="filter-header-group">
                    <span>Filter</span>
                    <div class="filter-toggle-btn click-cursor">
                        <i class="fas fa-angle-left"></i>
                    </div>
                </div>
                <div class="filter-header-group">
                    <button
                        class="green-button click-cursor filter-btn"
                    >
                        Apply
                    </button>

                    <button
                        class="green-button click-cursor filter-btn"
                    >
                        Reset
                    </button>
                </div>
            </div>
            <hr>

            <!-- Body -->
            <div class="filter-body">
                <!-- Search -->
                <div class="filter-search">
                    <input
                        type="text"
                        class="filter-search-input"
                        placeholder="Search by Land ID"
                    >
                </div>

                <!-- Status -->
                <div class="filter-status">
                    <span class="filter-heading">Status</span>
                    <div class="container">
                        <ul class="filter-status__list row">
                            <li
                                class="filter-status__item col c-6"
                                v-for="(status, index) in filterStatus"
                                :key="status"
                            >
                                <label class="status-label click-cursor" :for="'status-' + index">
                                    <input
                                        class="click-cursor"
                                        type="radio"
                                        name="status"
                                        :id="'status-' + index"
                                        :checked="index === 0"
                                    />
                                    <span>{{ status }}</span>
                                </label>
                            </li>
                        </ul>
                    </div>
                </div>

                <!-- Region -->
                <div class="filter-region">
                    <span class="filter-heading">Region</span>
                    <div class="container">
                        <ul class="filter-region__list row">
                            <li
                                class="filter-region__item col c-6"
                                v-for="(region, index) in filterRegion"
                                :key="region"
                            >
                                <label class="region-label click-cursor" :for="'region-' + index">
                                    <input
                                        class="click-cursor"
                                        type="checkbox"
                                        name="regions"
                                        :id="'region-' + index"
                                        :checked="index === 0"
                                    />
                                    <span>{{ region }}</span>
                                </label>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </template>
    </div>
</template>

<script>
import '../assets/grid.css'

export default {
    data() {
        return {
            isExpanded: true,
            filterStatus: ['All', 'For Sale', 'Not for sale', 'Vacant'],
            filterRegion: [
                'All',
                'Adelyn',
                'Adelyn Highlands',
                'Amber Town',
                'Amoriath\'s Domain',
                'Breakwater Island',
                'Dornielle Abbey',
                'Esterfork',
                'Fairling Forest',
                'Gaeron\'s Wood',
                'Haywoord',
                'Illyria\'s Rest',
                'Lake of Knives',
                'Old King\'s Barrow',
                'Riverhold',
                'Stefan\'s Lake',
                'Stillwood Meadow'
            ]
        }
    },

    methods: {
        expandFilter() {
            this.isExpanded = !this.isExpanded;
        }
    }
}
</script>

<style scoped>
.filter {
    flex: 0.25;
    height: 100%;
    margin-right: 30px;
    padding: 74px 50px 50px;
}

.filter-header-group {
    font-size: 18px;
    color: #3e1f05;
    position: relative;
    z-index: 1;
    display: flex;
    justify-content: space-between;
}

.filter-toggle-btn {
    font-size: 20px;
    padding: 0.5em 0;
    padding-left: 20px;
}

.filter-btn {
    width: 48%;
    margin: 0;
}

.filter-body {
    position: relative;
    height: calc(100% - 130px);
    overflow-y: auto;
    overflow-x: hidden;
    padding: 0 3px 3px;
    margin: 1em 0 0;
}

.filter-body::-webkit-scrollbar {
    width: 6px;
    padding: 3px 0;
}

.filter-body::-webkit-scrollbar-track {
    background-color: #eecba1;
    width: 4px;
    border-radius: 6px;
    border: 2px solid #eccca4;
}

.filter-body::-webkit-scrollbar-thumb {
    background-color: #ffe3bc;
    border-radius: 16px;
    margin: 2px 0;
    width: 6px;
    border-radius: 16px;
}

.filter-search {
    padding-bottom: 1em;
}

.filter-search-input {
    background-color: #eecba1;
    color: #3e1f05;
    height: 36px;
    width: 100%;
    outline: none;
    border: none;
    border-radius: 8px;
    padding: 3px 10px;
    font-family: Poppins;
    font-size: 18px;
    font-weight: 500;
}

.filter-search-input::placeholder {
    color: #c7a47d;
}

.filter-search-input:focus {
    border-width: 2px;
    border-style: solid;
    border-color: #dcbe98;
}

.filter-heading {
    font-family: "Lora", Georgia,serif;
    font-size: 18px;
    color: #3e1f05;
    font-weight: 700;
}

.filter-status__item,
.filter-region__item {
    margin-bottom: 10px;
}

.status-label,
.region-label {
    color: #3e1f05;
    font-family: "Lora", Georgia,serif;
    display: flex;
    align-items: center;
    /* width: fit-content; */
}

.status-label span,
.region-label span {
    display: block;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    max-width: 142px;
}

.status-label input,
.region-label input {
    position: relative;
    margin: 0;
    margin-right: 5px;
}

.status-label input::after,
.region-label input::after {
    content: "";
    position: absolute;
    top: -1px;
    left: -1px;
    right: -1px;
    bottom: -1px;
    background-color: #ffe3bd;
    border-width: 1px;
    border-style: solid;
    border-color: #000;
}

.status-label input::after,
.status-label input::before {
    border-radius: 50%;
}

.status-label input:checked::before,
.region-label input:checked::before {
    content: "";
    position: absolute;
    top: 1px;
    left: 1px;
    right: 1px;
    bottom: 1px;
    background-color: #066c45;
    z-index: 1;
}

hr {
    width: 100%;
    display: block;
    height: 1px;
    border: 0;
    border-bottom: 1px solid rgba(62,31,5,.1);
    margin: 1em 0 0;
}
</style>