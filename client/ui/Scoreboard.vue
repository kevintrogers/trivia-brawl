<template>
    <div class='col-4 col-offset-8'>
        <div class='row'>
                <span class='placard' id='player-placard'>YOU</span>
            </div>
            <div class='row'>
                <div class='health-meter col-10 col-offset-1' id='player-health-meter' :style="{width:playerHealth * 8 + '%' }"></div>
            </div>
            
        <div class='row'>
                <div class='placard' id='opponent-placard'><span>OPPONENT</span><img class='circle-img' src='http://media-cache-ak0.pinimg.com/736x/a0/b4/7b/a0b47bca16fb26652198608cf2135753.jpg'</span></div>
            </div>
            <div class='row'>
                <div class='health-meter col-10 col-offset-1' id='opponent-health-meter' :style="{width:opponentHealth * 8 + '%' }"></div>
        </div>
        
        <div class='row'>
            <span class='question-count'>Questions: {{questionCount}}</span>
        </div>
        
    </div>
    
</template>
<script>
export default {
    data() {
        return {
            
            questionCount: 0,
            playerHealth:10,
            opponentHealth:10,
            playerWin: false,
            opponentWin: false,
        }
    },
            methods: {
                calculateHealth: function() {
                    if (this.playerWin) {
                        this.opponentHealth -1;
                    }
                    if (this.OpponentWin) {
                        this.playerHealth -1;
                    }
                    this.playerWin, this.OpponentWin = false;
                }
            
            
        }
    };
    
</script>
<style>
    
</style>