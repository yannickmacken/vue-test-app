<template>
<li>
    <h2>{{ friendName }} {{ isFavorite ? '(favorite)' : ''}}</h2>
    <button @click="toggleDetails">show details</button>
    <button @click="toggleFavorite">favorite</button>
    <ul v-if="detailsAreVisible">
        <li><strong>Phone: </strong>{{ friendPhone }}</li>
        <li><strong>Id: </strong>{{ friendId }}</li>
        <li><strong>isFavorite: </strong>{{ isFavorite }}</li>
    </ul>
</li>
</template>

<script>
export default {
    // These props are passed down from parent component (App)
    props: [
        "friendId",
        "friendName",
        "friendPhone",
        "isFavorite"
    ],
    data() 
        {
        return {detailsAreVisible: false,}
    },
    methods: {
        toggleDetails() {
            this.detailsAreVisible = !this.detailsAreVisible
        },
        toggleFavorite() {
            this.$emit('toggle-favorite', this.friendId)
        }
    }
}
</script>

<styles>

</styles>