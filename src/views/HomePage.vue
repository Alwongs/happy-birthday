<template>
    <div class="home-page">
        <h1 :style="{ 'margin-right': gap + '%' }">Happy birthday</h1>
        <footer :style="{ 'margin-right': gap2 + '%' }">to you!!!</footer>
    </div>
</template>

<script>
export default {
    data() {
        return {
            gap: -200,
            gap2: -200
        }
    },
    methods: {
    move() {
        setInterval(() => {
            if(this.gap < 0) {
                this.gap++;
            }
        }, 10)
    },
    },
    mounted() {
        this.move();
    }
}
</script>

<style lang="scss">

.home-page {
    background-image: url('../assets/img/jpg/sea.jpg');
    background-size: cover;
    height: 100vh;
}
h1 {
    text-align: center;
    padding: 32px;
    font-size: 64px;
    color: white;
}

</style>