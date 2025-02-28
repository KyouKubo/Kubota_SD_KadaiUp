<script setup>
function getRandom( min, max ) {
    var random = Math.floor( Math.random() * (max + 1 - min) ) + min;
  
    return random;
}


const { data: trainers } = await useTrainers();
const route = useRoute();
const router = useRouter();
const config = useRuntimeConfig();
// const gosanke_url = [
//   `https://pokeapi.co/api/v2/pokemon/1/`,
//   `https://pokeapi.co/api/v2/pokemon/2/`,
//   `https://pokeapi.co/api/v2/pokemon/3/`
// ];
const gazo = "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/100.png"
const { data: pokemons1 } = await useFetch(
  () =>
  
    `https://pokeapi.co/api/v2/pokemon`,
  {
    default: () => [],
    server: false,
  },
)

const baseImageURL = "https://pokeapi.co/api/v2/pokemon/"
const pickNum = getRandom(1,1000);
const getURL = `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/${pickNum}.png`;
</script>

<template>
  <div>
    <h1>ポケットモンスター</h1>
    <!-- <p>{{ pokemons1.sprites.front_default }}</p> -->
    <img src="/avatar.png" />
    <!-- <p>{{ pickNum }}</p>
    <p>{{ getURL }}</p> -->
    <!-- <p>{{ pokemons1.results[pickNum].name }}</p> -->
    <img :src="getURL"/>
    <GamifyList>
      <GamifyItem v-if="trainers.length > 0">

        
        <NuxtLink to="/trainer">つづきからはじめる</NuxtLink>
      </GamifyItem>
      <GamifyItem v-else>
        <span>つづきからはじめる</span>
      </GamifyItem>
      <GamifyItem>
        <NuxtLink to="/new">あたらしくはじめる</NuxtLink>
      </GamifyItem>
    </GamifyList>
  </div>
</template>
