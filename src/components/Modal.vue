<template>
    <div
        v-if="this.isOpen"
        class="modal-overlay"
    >
        <div class="modal">
            <div
                class="close-btn click-cursor"
                @click="this.toggleModal()"
            ></div>

            <h3 class="modal-title">{{ this.title }}</h3>

            <div class="modal-button-list">
                <button
                    class="modal-button click-cursor"
                    v-for="btn in this.buttons"
                    :key="btn.title"
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
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 2000;
    background-color: rgba(0, 0, 0, 0.2);
    display: flex;
}

.modal {
    position: relative;
    background-image: url("../assets/images/modal.png");
    background-repeat: no-repeat;
    background-size: contain;
    background-position: center;
    margin: auto;
    width: 500px;
    height: 190px;
}

.close-btn {
    background-image: url("../assets/images/close-modal-btn.png");
    background-repeat: no-repeat;
    background-size: contain;
    position: absolute;
    top: 21px;
    right: 20px;
    width: 34px;
    height: 34px;
}

.close-btn:hover {
    opacity: 0.9;
}

.modal-title {
    text-align: center;
    font-size: 14px;
    margin-top: 30px;
    color: #764d43;
}

.modal-button-list {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 30px;
}

.modal-button {
    background-image: url("../assets/images/modal-btn.png");
    background-repeat: no-repeat;
    background-size: cover;
    background-color: #066c45;
    border-radius: 6px;
    color: #ffe3bc;
    width: 130px;
    height: 26px;
    font-size: 12px;
    margin: 2px 0;
}

.modal-button:hover {
    background-color: #00984b;
}

@media (max-width: 376px) {
    .modal {
        background-image: url("../assets/images/responsive-modal.png");
        width: 100vw;
        height: 350px;
    }

    .modal-title {
        font-size: 18px;
        margin-top: 90px;
        color: #764d43;
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