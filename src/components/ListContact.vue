<template>
    <div class="container-list-contacts overflow-auto">
        <ul class="list-unstyled">
            <li @click="getActiveClick(index)" :class="(index == activeClick)? 'selected-gray' : ' ' "  v-for="(contact,index) in  checkSearchContact" :key="index">
                <div class="my-contact-wrapper d-flex justify-content-between">
                    <div class="my-contact-left d-flex">
                        <div class="my-pic-bg me-2">
                            <!-- <img :src="'img/' + contact.image" alt="foto"> -->
                            <img :src="contact.image" alt="img">

                        </div>
                        <div class="my-contact-text">
                            <h6 class="fw-bolder m-0">{{contact.name}}</h6>
                            <p class="m-0 my-last-msg">Ultimo messaggio</p>
                            <!-- <p  v-for="(msg,indexMsg) in contact.messages" class="m-0 my-time align-self-end">{{msg.date}}</p> -->
                            <p  v-if="contact.messages.length > 0"  class="m-0 my-time align-self-end">{{contact.messages[contact.messages.length - 1].date}}</p>
                        </div>
                    </div>
                </div>
            </li>
            
        </ul>

    </div>
</template>

<script>
export default {
name:"ListContact",


}
</script>

<style>

</style>