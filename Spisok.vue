<template>
    <div>
    <a v-if="vision" id="web2">
        <input type="date" style="margin-left: 10px" v-model="vremy">
        <!--      <img alt="Vue logo" src="./assets/logo.png">-->
        <label>
            <input v-model="shaurma" type="text" placeholder="писать тут" size="100"  v-on:keyup.enter="plov" style="border-radius: 5px">
            <button v-on:click="plov" style="border-radius: 5px; size: 100px"> <i class="fas fa-arrow-alt-circle-right"></i>  </button>
            <!--          <input type="button" size="50" value="тык" v-on:click="plov">-->
            <input type="button" value="другой список" @click="voda">
        </label>
        <ul type="radio">
            <li v-for="(her2, index) in dich2" :key="her2.message">
                <input type="checkbox" v-model="her2.done" v-on:change="gazirovka(index)" class="fas fa-check-circle" style="color: black">
                <s v-if="her2.done">{{index+1}} : {{her2.message}}</s>
                <span v-else> {{her2.message}}  </span>
                <button v-on:click="kefir2(her2.index)" class="del"> <i class="fas fa-trash-alt" style="color: white"></i> </button>
                <!--            <input type="button" value="×" v-on:click="kefir2(her2.index)" class="del">-->
            </li>
            <input type="button" value="Удалить все"  v-on:click="moloko2" class="button">
            <input type="button" value="Выделить все" @click="mineralka2" class="button">
        </ul>
    </a>
    </div>
</template>

<script>
    export default {
        name: "Spisok"
    }
</script>

<style scoped>

</style>