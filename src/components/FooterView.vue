<template>
    <footer class="footer">
        <div class="container">
            <span>Mavulus &copy; {{ currentYear }}</span>
        </div>
    </footer>
</template>

<script>
export default {
    data() {
        return {
            currentYear: new Date().getFullYear()
        }
    }
}
</script>

<style>
.footer {
    bottom: 0;
    width: 100%;
    height: 60px;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: var(--color-background);
    box-shadow: 0px -2px 4px rgba(0, 0, 0, 0.2);
}

.container {
    text-align: center;
}
</style>
