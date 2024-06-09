<template>
    <div>
        <div>{{ name }}</div>
        <div>{{ cpf }}</div>
    </div>
</template>

<script>
    export default {
        name: 'PersonData',
        props: {
            compName: String,
            compCPF: String,
        },
        data() {
            return {
                name: '',
                cpf: ''
            }
        },
        mounted() {
            this.name = this.compName;
            this.cpf = this.compCPF;
        }
    }
</script>
