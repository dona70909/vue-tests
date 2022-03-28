<template>
    <header class="container-fluid">
        <div class="row p-4">
            <div class="col-12">
                <h2>ciao</h2>
                <Paragraph/>
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