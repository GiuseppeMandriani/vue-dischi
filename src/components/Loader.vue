<template>
    <div class="loader">
        <img src="@/assets/logo.png" alt="Logo Spotify" />
        <div class="text">Caricamento...</div>
    </div>
</template>

<script>
export default {
    name: 'Loader',
};
</script>

<style scoped lang="scss">
@import '@/styles/vars';
.loader {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba($primary-color, 0.9);
    .text {
        text-transform: uppercase;
        color: rgba($brand-color, 0.5);
    }
}
img {
    width: 70px;
    margin-bottom: 1rem;
    animation: pulse 1s infinite alternate;
}

@keyframes pulse {
    from {
        transform: scale(1);
    }
    to {
        transform: scale(1.2);
    }
}
</style>
