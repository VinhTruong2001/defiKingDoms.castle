<template>
    <div
        v-if="isOpen"
        :class="`modal-overlay overlay ${isOpen ? 'active' : ''}`"
    >
        <div
            class="modal game-border fancy"
            :style="{
                width: width + 'px',
                height: height + 'px',
            }"
        >
            <div
                class="close-btn click-cursor"
                @click="toggleModal()"
            ></div>

            <h3 class="modal-title fancy" v-if="fancyTitle">
                <span>{{ fancyTitle }}</span>
            </h3>

            <h3 class="modal-title basic" v-if="title">
                <span>{{ title }}</span>
            </h3>

            <div class="modal-body">
                <slot></slot>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    props: [
        'fancyTitle',
        'title',
        'buttons',
        'width',
        'height',
    ],

    data() {
        return {
            isOpen: false,
        }
    },

    methods: {
        toggleModal() {
            this.isOpen = !this.isOpen;
        },
    }
}
</script>

<style scoped>
.modal-overlay {
    z-index: -1;
    opacity: 0;
    will-change: opacity;
    transition: all 0.5s linear;
}

.modal-overlay.active {
    z-index: 2000;
    opacity: 1;
    will-change: opacity;
    transition: all 0.5s linear;
}

.modal {
    margin: auto;
    padding: 50px 50px 70px;
}

.modal-title {
    color: #764d43;
    text-align: center;
    margin-bottom: 0;
}

.modal-title.basic {
    font-size: 28px;
    font-family: "Lora",Georgia,serif;
    font-weight: 400;
}

.modal-title.fancy {
    position: relative;
    top: -42px;
    font-size: 16px;
    margin-top: 30px;
    color: #764d43;
    background-image: url('../assets/images/borders/modal-title-middle.png');
    background-repeat: repeat-x;
    margin: 0 auto;
    height: 70px;
    width: 130px;
    display: flex;
    align-items: center;
    justify-content: center;
}

.modal-title.fancy::before {
    content: "";
    position: absolute;
    display: block;
    width: calc(100% + 60px);
    top: 0;
    left: -30px;
    height: 100%;
    background-image: url('../assets/images/borders/modal-title-left.png'),
        url('../assets/images/borders/modal-title-right.png');
    background-repeat: no-repeat;
    background-position: 0 0,100% 0;
}

.modal-body {
    position: relative;
    z-index: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
}

@media (max-width: 376px) {
    .modal {
        width: 100vw;
    }

    .modal-title.fancy {
        width: 90px;
    }

    .close-btn {
        top: 35px;
        right: 28px;
        width: 48px;
        height: 48px;
    }

    .modal-button {
        border-radius: 9px;
        width: 200px;
        height: 41px;
        font-size: 14px;
    }
}
</style>