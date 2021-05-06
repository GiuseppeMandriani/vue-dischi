<template>
    <div class="card-content">
        <div class="card-img">
            <img :src="details.poster" :alt="details.title" />
        </div>
        <div class="content-details">
            <span class="details-text">{{ details.title }}</span>
            <span class="details-text gray">{{ details.author }}</span>
            <span class="details-text gray">{{ details.year }}</span>
            <span class="details-text">{{ details.genre }}</span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['details'],
};
</script>

<style scoped lang="scss">
.card-content {
    height: 100%;
}
.card-img {
    width: 100%;
    height: 50%;
    img {
        max-width: 100%;
    }
}

.content-details {
    text-align: center;
    .details-text {
        display: block;
        font-size: 0.7rem;
        margin: 0.5rem 0;
        &:first-child {
            font-size: 0.8rem;
            text-transform: uppercase;
            font-weight: 500;
            margin: 0.5rem 0;
        }

        &:last-child {
            margin-bottom: 0;
        }
    }

    .details-text.gray {
        color: #6a6e75;
    }
}
</style>
