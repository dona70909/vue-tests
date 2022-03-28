<template>
    <div  class="my-contact-wrapper d-flex justify-content-between px-2 py-3 selected-gray">
        <div class="my-contact-left d-flex">
            <div class="my-pic-bg me-2">
                <img :src="'img/' + contact.image" alt="foto">
            </div>
            <h5>{{contact.name}}</h5>
        </div>
        
        <div class="my-contact-right">
            <i class="bi bi-search fs-4 icon-grey"></i>
            <i class="bi bi-paperclip fs-4 icon-grey"></i>
            <i class="bi bi-three-dots-vertical fs-4 icon-grey"></i>
        </div>
    </div>
</template>

<script>
export default {
    name:"SelectedContact",
}
</script>

<style>

</style>