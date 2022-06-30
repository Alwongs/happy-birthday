<template>
    <div class="home-page">
        <header>
            <h1 :style="{ 'margin-right': gap + '%' }">Happy birthday</h1>
        </header>
        <canvas id="game" width="300" height="200"></canvas>
        <footer>
            <h1 :style="{ 'margin-left': gap2 + '%' }">to you!</h1>
        </footer>
    </div>
</template>

<script>
export default {
    data() {
        return {
            gap: -200,
            gap2: -200,
            x: 0,
            y: 100,
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
                if(this.gap === 0 && this.gap2 === 0) {
                    this.drawSmileFirst();
                }
            }, 10)
        },
        drawSmileFirst() {
            const canvas = document.getElementById('game');
            const ctx = canvas.getContext('2d');       
            ctx.fillStyle = "red";
            setInterval(() => {
                if ( this.y < 185 && this.x < 100) {                    
                    ctx.fillRect(this.x, this.y, 15, 15);
                    this.y++;
                    this.x++;
                } else {
                    this.drawSmileSecond();
                }
            }, 100);
        },
        drawSmileSecond() {
            const canvas = document.getElementById('game');
            const ctx = canvas.getContext('2d');       
            ctx.fillStyle = "red";
            setInterval(() => {
               if (this.y === 185 && this.x < 200) {
                    ctx.fillRect(this.x, this.y, 15, 15);
                    this.x++;
                } else {
                    this.drawSmileThird();
                }
            }, 100);            
        },
        drawSmileThird() {
            const canvas = document.getElementById('game');
            const ctx = canvas.getContext('2d');       
            ctx.fillStyle = "red";
            setInterval(() => {
               if (this.x >= 200 && this.x < 285) {
                    ctx.fillRect(this.x, this.y, 15, 15);
                    this.y--;
                    this.x++;
                } else {
                    this.drawLeftEye();
                }
            }, 100);            
        },
        drawLeftEye() {
            const canvas = document.getElementById('game');
            const ctx = canvas.getContext('2d');       
            ctx.fillStyle = "blue";
            this.x = 120;
            this.y = 80;
            setInterval(() => {
               if (this.y > 20) {
                    ctx.fillRect(this.x, this.y, 15, 15);
                    this.y--;
                } else {
                    this.drawRightEye();
                }
            }, 500);            
        },
        drawRightEye() {
            const canvas = document.getElementById('game');
            const ctx = canvas.getContext('2d');       
            ctx.fillStyle = "blue";
            this.x = 180;
            this.y = 80;
            setInterval(() => {
               if (this.y > 20) {
                    ctx.fillRect(this.x, this.y, 15, 15);
                    this.y--;
                } else {
                    return;
                }
            }, 500);            
        },
    },
    mounted() {
        this.move();
    }
}
</script>

<style lang="scss">

.home-page {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    background-image: url('../assets/img/jpg/sea.jpg');
    background-size: cover;
    height: 100vh;
}
h1 {
    text-align: center;
    padding: 32px;
    font-size: 128px;
    color: yellow;
    @media (min-width: 1024px) and (max-width: 1440px) {
        font-size: 86px;
    }     
    @media (min-width: 768px) and (max-width: 1024px) {
        font-size: 64px;
    }      
    @media (max-width: 768px) {
        font-size: 64px;
    }     
}
footer {
    
}
#game {
    width: 300;
    height: 200;
    margin: 0 auto;
}
</style>