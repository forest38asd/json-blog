<template>
    <div class="navigate">
        <button @click="prevPage" :disabled="$parent.pageNumber === 0">
            Previous
        </button>
        <button @click="chosePage(index)"
                v-for="index in $parent.pageCount"
                :key="index"
                :disabled="$parent.pageNumber+1 === index"
        >
            {{ index }}
        </button>
        <button @click="nextPage" :disabled="$parent.pageNumber >= this.$parent.pageCount - 1">
            Next
        </button>
    </div>
</template>

<script>
    export default {
        name: "test",
        methods: {
            nextPage(){
                this.$parent.pageNumber++;
            },
            prevPage(){
                this.$parent.pageNumber--;
            },
            chosePage(page){
                this.$parent.pageNumber = page-1
            }
        }
    }
</script>

<style scoped>
    .navigate {
        width: 25%;
        padding: 0.2rem 0.2rem;
        margin: 0.5rem auto;
        display: flex;
        justify-content: space-around;
    }
    button {
        height: 1.5rem;
        width: 5rem;
    }
</style>
