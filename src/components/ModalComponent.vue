<template>
    <div class="modal" v-if="show">
        <div class="modal-overlay" @click="close"></div>
        <div class="modal-container">
            <div class="modal-header">
                <h2>{{ title }}</h2>
                <button class="modal-close" @click="close">&times;</button>
            </div>
            <div class="modal-body">
                <p class="date">{{ date }}</p>
                <p class="short-text">{{ text }}</p>
                <hr>
                <ul>
                    <li v-for="image in images" :key="image.id">
                        <img :src="image">
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        show: {
            type: Boolean,
            required: true
        },
        title: {
            type: String,
            default: ''
        },
        date: {
            type: String,
            default: ''
        },
        text: {
            type: String,
            default: ''
        },
        images: {
            type: Array,
            default: () => []
        }
    },
    methods: {
        close() {
            this.$emit('close');
        }
    }
};
</script>

<style scoped>
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 9999;
}

.modal-overlay {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
}

.modal-container {
    position: relative;
    width: 80%;
    max-width: 600px;
    background-color: #fff;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    color: var(--color-background);
}
.date {
    font-size: 1rem;
    font-family: 'Lato-Bold', sans-serif;
    color: var(--color-text);
}

.modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem;
    border-bottom: 1px solid #ccc;
}

.modal-close {
    font-size: 2rem;
    font-weight: bold;
    color: #ccc;
    background-color: transparent;
    border: none;
    cursor: pointer;
}

.modal-body {
    padding: 1rem;
}

.modal-body p {
    margin-bottom: 1rem;
}

.modal-body ul {
    list-style: none;
    margin: 0;
    padding: 0;
}

.modal-body li {
    margin-bottom: 1rem;
}

.modal-body img {
    max-width: 100%;
    height: auto;
}
</style>
