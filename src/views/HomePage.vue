<template>
    <div class="home-page">
        <h1 :style="{ 'margin-right': gap + '%' }">Happy birthday</h1>
        <footer>
            <h1 :style="{ 'margin-left': gap2 + '%' }">to you!!!</h1>
        </footer>
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
                if(this.gap === 0) {
                    if(this.gap2 < 0) {
                        this.gap2++;
                    }                    
                }
            }, 10)
        }
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
    font-size: 128px;
    color: white;
}

</style>