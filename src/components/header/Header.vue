<template>
    <header class="container-fluid">
        <div class="row p-4">
            <div class="col-12">
                <h1>header</h1>
                <Paragraph/>
                <button v-for="audio in audios" :key="audio.id" @click.prevent="audio.isPlaying ? pause(audio) : play(audio)"  class="btn btn-primary" @dblclick="stopSound">
                    play!
                </button>
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
    },

    data(){
        return{
            audios:[
                {
                    id: '1',
                    name: 'Fibra',
                    file: new Audio(require('@/assets/X2Download.com - Fabri Fibra, Colapesce, Dimartino - Propaganda (Official Video) (128 kbps).mp3')),
                    isPlaying: false
                }
            ],
        }
    },


    methods: {
        play (audio) {
            audio.isPlaying = true;
            audio.file.play();
        },
    
        pause (audio) {
            audio.isPlaying = false;
            audio.file.pause();
        }
    }

}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/style.scss";

h1{
    color:$mainColor;
}
</style>