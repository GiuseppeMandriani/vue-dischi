<template>
    <header class="container">
        <!-- Logo -->
        <div class="logo">
            <img src="@/assets/logo.png" alt="Logo Spotify" />
            <h1>{{ message }}</h1>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header',
    props: ['message'],
};
</script>

<style scoped lang="scss">
@import '@/styles/vars.scss';

.logo {
    display: flex;
    align-items: center;
    height: 70px;
    /* padding: 10px 10px; */
    h1 {
        font-size: 1.5rem;
        margin-left: 1rem;
        font-weight: 400;
        letter-spacing: 2px;
    }
}
.logo img {
    width: 50px;
}
</style>
