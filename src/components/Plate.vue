<template>
    <div class="plate">
        <div class="title">
            <h1>{{ article.title }}</h1>
        </div>
        <div class="body">
            <p>
                {{ article.body }}
            </p>
        </div>
        <div class="author">
            {{ user.name }}
        </div>
    </div>
</template>

<script>
    export default {
        name: "Plate",
        props: {
            article: {
                type: Object,
                require: true,
            },
            users: {
                type: Object,
                require: true,
            },
            user: {
                type: Object,
                require: true
            }
        }
    }
</script>

<style scoped>
    .plate {
        width: 80%;
        min-height: 11rem;
        border: solid 1px black;
        border-radius: 1rem;
        display: flex;
        flex-direction: column;
        margin: 0 auto 0.5rem;
        padding: 1rem;
        text-align: left;
    }
</style>
