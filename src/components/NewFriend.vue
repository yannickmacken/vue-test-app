<template>
    <form @submit.prevent="onSubmit">
        <div>
            <label>name</label><br>
            <input v-model="name" type="text"><br>
        </div>
        <div>
            <label>phone</label><br>
            <input v-model="phone" type="tel"><br>
        </div>
        <div>
            <button>add contact</button><br>
        </div>
    </form>
</template>

<script>
    export default {
        emits: ['new-friend-data'],
        data() {
            return {
                name: "",
                phone: ""
            }
        },
        methods: {
            onSubmit() {
                console.log("hello")
                this.$emit('new-friend-data', this.name, this.phone)
            }
        }
    }
</script>

<styles>

</styles>