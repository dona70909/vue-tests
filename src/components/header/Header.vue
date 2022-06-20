<template>
    <header class="container-fluid">
        <div class="row p-4">
            <div class="col-12">
                <h2>ciao</h2>
                <Paragraph/>
<<<<<<< HEAD
                <button v-for="audio in audios" :key="audio.id" @click.prevent="audio.isPlaying ? pause(audio) : play(audio)"  class="btn btn-primary" @dblclick="stopSound">
                    play!
                </button>
                <h3>prova</h3>
=======
>>>>>>> parent of 444f407 (audio)
            </div>
        </div>
    </header>
</template>

<script>
import Paragraph from "./Paragraph.vue"


export default {
    name:"HeaderTest",
    components:{
        Paragraph,
    }

}
</script>

<style>

</style>