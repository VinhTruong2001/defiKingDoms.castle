<template>
    <div
        :class="`modal-overlay overlay ${this.isOpen ? 'active' : ''}`"
    >
        <div class="modal game-border fancy">
            <div
                class="close-btn click-cursor"
                @click="this.toggleModal()"
            ></div>

            <h3 class="modal-title">
                <span>{{ this.title }}</span>
            </h3>

            <div class="modal-button-list">
                <button
                    class="green-button click-cursor"
                    v-for="btn in this.buttons"
                    :key="btn.title"
                    @click="btn.click()"
                >
                    {{ btn.title }}
                </button>
            </div>

        </div>
    </div>
</template>

<script>
export default {
    props: ['title', 'buttons'],

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
    width: 600px;
    height: 250px;
}

.modal-title {
    position: relative;
    top: 10px;
    text-align: center;
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

.modal-title::before {
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

.modal-button-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 30px;
}

.modal-button-list button {
    min-width: 200px;
    margin: 5px 0;
}

@media (max-width: 376px) {
    .modal {
        width: 100vw;
        height: 350px;
    }

    .modal-title {
        width: 90px;
    }

    .close-btn {
        top: 35px;
        right: 28px;
        width: 48px;
        height: 48px;
    }

    .modal-button-list {
        margin-top: 60px;
    }

    .modal-button {
        border-radius: 9px;
        width: 200px;
        height: 41px;
        font-size: 14px;
    }
}
</style>