<template>
    <div class="controllers">
        <button @click="diceRoll" class="dice">Push me</button>
        <span class="results">result: {{ result }}</span>
        <span class="position">position player 1: {{ position }}</span>
        <span class="position">position player 2: {{ position2 }}</span>
    </div>
    <div>
        <table class="tabla">
            <tr v-for="n in 7" :key="n">
            <td v-for="m in 9" :key="m"
            :id="'casilla'+(((n - 1)*10) + (m))"
            :style="'background-color: '+colors[(((n - 1)*10) + m)]+';'"
            class="place">{{ n - 1 }}{{ m * 1 }}
            </td>
            </tr>
        </table>
    </div>
    <div class="demo" ref=""
    :style="'background-color:'+color+';'
    +'font-size:30px; color:white; margin-top: 10px;'">{{ msg }}</div>
</template>
<script>
export default{
    data(){
        return{
            result: 0,
            position: 1,
            position2:1,
            isActive: false,
            activeClass: 'active',
            errorClass: 'place',
            msg: '',
            color: 'green',
            colors:['','','','','','','','','','',
                    '','','','','','','','','','',
                    '','','','','','','','','','',
                    '','','','','','','','','','',
                    '','','','','','','','','','',
                    '','','','','','','','','','',
                    '','','','','','','','','']
        }
    },
    methods: {
        diceRoll(){
            this.isActive = !this.isActive
            console.log(this.isActive)
            var dice = Math.round((Math.random() * 5) + 1);
            console.log(dice)
            this.msg = ''
            if (this.isActive){
            if (this.position == this.position2){
                this.colors[this.position] = 'blue'
            } else {
            this.colors[this.position] = '';
            }
            this.result = dice;
            this.position += dice;
            switch (this.position) {
                case 12:
                    this.position = 51
                    this.msg = 'jugador 1 avanza a casilla ' +this.position
                    this.color = 'green'
                    break;
                case 19:
                    this.position = 1
                    this.color = 'red'
                    this.msg = 'jugador 1 desciende a casilla ' +this.position
                    break;
                case 22:
                    this.position = 3
                    this.color = 'red'
                    this.msg = 'jugador 1 desciende a casilla ' +this.position
                    break;
                case 33:
                    this.position = 21
                    this.color = 'red'
                    this.msg = 'jugador 1 desciende a casilla ' +this.position
                    break;
                case 59:
                    this.position = 67
                    this.color = 'green'
                    this.msg = 'jugador 1 avanza a casilla ' +this.position
                    break;
                case 61:
                    this.position = 69
                    this.color = 'green'
                    this.msg = 'jugador 1 avanza a casilla' +this.position
                    break;
                default:
                    break;
            }
            if(this.position >= 69){
                this.color = 'green'
                this.colors[69] =  'green'
                this.msg = 'Felicidades has ganado jugador 1'
            }
            this.colors[this.position] = 'green';
            } else {
            if (this.position == this.position2){
            this.colors[this.position2] = 'green'
            } else {
            this.colors[this.position2] = '';
            }
            this.result = dice;
            
            this.position2 += dice;
            switch (this.position2) {
                case 12:
                    this.position2 = 51
                    this.color = 'green'
                    this.msg = 'jugador 2 avanza a casilla ' +this.position2
                    break;
                case 19:
                    this.position2 = 1
                    this.color = 'red'
                    this.msg = 'jugador 2 desciende a casilla ' +this.position2
                    break;
                case 22:
                    this.position2 = 3
                    this.color = 'red'
                    this.msg = 'jugador 2 desciende a casilla ' +this.position2
                    break;
                case 33:
                    this.position2 = 21
                    this.color = 'red'
                    this.msg = 'jugador 2 desciende a casilla ' +this.position2
                    break;
                case 59:
                    this.position2 = 67
                    this.color = 'green'
                    this.msg = 'jugador 2 avanza a casilla ' +this.position2
                    break;
                case 61:
                    this.position2 = 69
                    this.color = 'green'
                    this.msg = 'jugador 2 avanza a casilla ' +this.position2

                    break;
                default:
                    break;
            }
            if(this.position2 >= 69){
                this.color = 'green'
                this.colors[69] =  'blue'
                this.msg = 'Felicidades has ganado jugador 2'
            }
            this.colors[this.position2] = 'blue';
            }
        }
    }
}
</script>
<style scoped>
.controllers{
    margin: 10px;
    padding: 20px;
    .dice, .results, .position{
        margin: 10px;
        border: solid black 3px;
        border-radius: 10px;
        font-size: 20px;
        padding: 30px;
    }
}
.tabla{
    align-items: center;
    margin: auto;
    /* background-image: url('./../assets/python.webp'); */

}
.place{
    padding: 25px;
    margin: 50px;
    border-radius: 10px;
    box-shadow: 2px 2px 2px 1px rgba(0, 0, 0, 0.2);
    font-size: 20px;
    
}
.active{
    background-color: red;
}

    #casilla22, #casilla19, #casilla33{
        color: white;
        background-image: url('./../assets/python.webp');
        background-size: 140px;
    }
    #casilla59, #casilla61, #casilla12{
        background-image: url('./../assets/leadder.avif');
        background-size: 160px;
    }
    
    

</style>