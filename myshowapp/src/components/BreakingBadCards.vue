<script setup>
    import axios from "axios"
    import { ref, watch,onMounted } from "vue";
    import Card from "./Card.vue"

    const characters = ref(null);
    const page = ref(0)
    //https://swapi.dev/
    //https://dev.to/monicafidalgo/12-apis-that-you-as-a-developer-will-love-it-4ec6

    
    onMounted(async () => {
        const response = await axios.get("https://random-data-api.com/api/v2/users?size=10&page=1&limit=1");
        characters.value = response.data;
        console.log(characters.value)
    })
    watch(
        page,async ()=>{
            const res = await axios.get(`https://random-data-api.com/api/v2/users?size=10&page=${page.value}&limit=1`);
            characters.value = res.data;
            console.log(characters.value)
        }
    )

    

</script>

<template>
    <div class="container">
        <div class="cards">
            <Card 
                v-for="character in characters"
                :key="character.id"
                :image="character.avatar"
                :name="character.first_name"
            >
                <div class="jobs">
                    <p>
                        <span> {{ character.date_of_birth }}</span>
                    </p>
                </div>
            </Card>
        </div>
        <div class="button-container">
            <button @click="page--">&lt</button>
            <button @click="page++">></button>
        </div>
    </div>
</template>

<style scoped>
.container {
    background-color: rgb(27, 26, 26);
    padding: 30px
}
.cards {
    max-width: 1000px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    height: 700px
}
.cards h3 {
    font-weight: bold;
}
.cards p {
    font-size: 10px;
}

.button-container {
    display: flex;
    justify-content: center;
    padding-top: 30px
}
.button-container button {
    border: none;
    width: 50px;
    height: 50px;
    border-radius: 100%;
    margin: 0 5px;
    cursor: pointer;
}
.spinner {
    display: flex;
    align-items: center;
    justify-content: center;
}

p {
    font-size: 10px;
}

.jobs {
    display: flex;
    flex-wrap: wrap;
}

</style>