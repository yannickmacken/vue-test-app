<template>
  <section alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
  <section>
    <h2>add friend</h2>
    <button @click="toggleAddFriend">add friend</button>
    <new-friend 
      v-if="addFriendStatus"
      @new-friend-data="addNewFriend"
    ></new-friend>
    <h2>contact list</h2>
    <ul>
      <friend-contact
        v-for="friend in friends"
        :key="friend.id"
        :friend-id="friend.id"
        :friend-name="friend.name"
        :friend-phone="friend.phone" 
        :is-favorite="friend.isFavorite"
        @toggle-favorite="toggleFavoriteStatus"
      >
      </friend-contact>
    </ul>
  </section>
  </section>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

export default {
  data() {
    return {
      friends: [{
        id: 'manuel',
        name: 'm lorenz',
        phone: '18209387',
        isFavorite: false
      },
      {
        id: 'pedro',
        name: 'p lorenz',
        phone: '2342343',
        isFavorite: false
      }],
      addFriendStatus: false
    }
  },
  methods: {
    toggleFavoriteStatus(friendId) {
      const identifiedFriend = this.friends.find(friend => friend.id === friendId)
      identifiedFriend.isFavorite = !identifiedFriend.isFavorite 

    },
    toggleAddFriend() {
      this.addFriendStatus = ! this.addFriendStatus
    },
    addNewFriend(name, phone) {
      this.friends.push({
        id: name,
        name: name,
        phone: phone
      })
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');

* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>
