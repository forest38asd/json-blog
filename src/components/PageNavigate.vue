<template>
    <div class="navigate">
        <button @click="prevPage" >
            Previous
        </button>
        <button @click="chosePage(index)"
                v-for="index in pageNumber + (pageNumber<3 ? 5-pageNumber : 3)"
                :key="index"
                :disabled="pageNumber+1===index"
        >
            {{ index }}
        </button>
        <button @click="nextPage" :disabled="pageNumber >= pageCount -1">
            Next
        </button>
    </div>
</template>

<script>
    export default {
        name: "PageNavigate",
        methods: {
            nextPage(){
                this.$parent.pageNumber++;
            },
            prevPage(){
                this.$parent.pageNumber--;
            },
            chosePage(page){
                this.pageNumber = page-1
            }
        },
        props: {
            pageNumber: this.$parent.pageNumber,
            pageCount: this.$parent.pageCount
        }
    }
</script>

<style scoped>
    .navigate {
        width: 20%;
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
