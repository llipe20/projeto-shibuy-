<template>
    <div class="box-modal">
        <p>{{ msg }}</p>
    </div>
</template>

<script>
export default {
    name : 'Modal',

    props : {
        msg : String
    }
}
</script>

<style scoped>
    .box-modal {
        color: #004085;
        background-color: #CCE5FF;
        border: 2px solid #B8DAFF;
        border-radius: 10px;
        padding: 10px;
        width: 400px;
        font-size: 1.15em;
        margin: auto auto 20px auto;
        transition: .5s;
    }
</style>