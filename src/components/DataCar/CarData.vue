<template>
    <div>
        <div v-for="info in query" :key="info.placa"> 
            {{ info.placa }} <br>
            {{ info.ano }} <br>
            {{ info.mensalidade }} <br>
        </div>
    </div>
</template>

<script>
export default {
    name: 'CarData',
    props: {
        compQuery: {
            type: Array,
            required: true
        }
    },
    data() {
        return {
            query: []
        }
    },
    mounted() {
        this.query = this.compQuery;
    }
}
</script>
