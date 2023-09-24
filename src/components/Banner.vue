<template>
    <div class="box-banner" :style="banner">
        <div class="box-text">
            <h1>Projeto Shibuya</h1>
            <p>
                Lorem ipsum, dolor sit amet consectetur adipisicing elit. Nulla illo natus, blanditiis sapiente repellendus quidem veritatis optio, totam neque cumque ex fugiat maiores eveniet consequatur libero quasi aperiam. Ad, quam.
            </p>
        </div>
    </div>
</template>

<script>
export default {
    nome : 'Banner',

    props : ["banner"]
}

</script>

<style scoped>
    .box-banner {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        background-position: 0 -250px;
        background-size: cover;
        padding: 30px;
        width: 100%;
        height: 600px;
    }

    .box-text {
        display: flex;
        flex-direction: column;
        align-items: flex-start;
        justify-content: center;
        background-color: #2222229e;
        width: 42vw;
        height: auto;
        padding: 15px;
    }

    .box-banner h1 {
        color: white;
        font-size: 3em;
    }

    p {
        color: white;
        text-align: justify;
        line-height: 1.5em;
        font-size: 1.4em;
    }
</style>