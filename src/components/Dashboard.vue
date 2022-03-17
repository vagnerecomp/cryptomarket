<template>
    <div class="table-row-heading">
        <div>Name</div>
        <div>Price</div>
        <div>1h %</div>
        <div>Market Cap</div>
        <div>Volume</div>
    </div>

    <div class="table-row" v-for="coinData in coinsData" :key="coinData.id">
        <div class="coin-presentation-field">
            <img :src="coinData.image" alt="Coin image" id="coin-image">
            <div id="coin-name"><p>{{coinData.name }}</p></div>
            <div> <p id="coin-symbol">{{coinData.symbol}}</p> </div>
        </div>
        <div id="coin-price"> ${{coinData.current_price}} </div>
        <div
            v-if="coinData.price_change_percentage_24h >= 0" style="color: #10b981;" class="coin-change"> {{coinData.price_change_percentage_24h}}% 
        </div>
        <div v-else style="color: #ef4444;" class="coin-change">
            {{coinData.price_change_percentage_24h}}% 
        </div>
        <div> ${{coinData.market_cap}} </div>
        <div> {{coinData.total_volume}} </div>
    </div>
</template>

<script>
export default {
    name: "Dashboard",
    data (){
        return{
            coinsData: null
        }
    },
    methods:{
        async getCoinsData(){
            const req = await fetch("https://api.coingecko.com/api/v3/coins/markets?vs_currency=usd&order=market_cap_desc&per_page=100&page=1&sparkline=false&price_change_percentage=1h");
            const data = await req.json();
            this.coinsData = data;
            console.log(this.coinsData);
        }
    },
    mounted(){
        this.getCoinsData();
    }
}
</script>

<style scoped>
.table-row, .table-row-heading {
    /* background-color: rgb(24 255 255); */
    min-width: 93%;
    height: 57px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;

}
.table-row div, .table-row-heading div{
    width: 20%;
}
.table-row-heading{
    background-color: #dcdcdc;
}
.table-row-heading div{
    color: #4B5563;
    font-weight: 600;
}
.table-row-heading div:nth-child(1){
    padding-left: 16px;
}
.coin-presentation-field{
    display: flex;
    justify-content: space-around;
}
.coin-presentation-field div{
    margin-left: 8px;
}
#coin-image{
    width: 20px;
    height:20px;
}
#coin-name, #coin-price, .coin-change{
    font-weight: bold;
}
#coin-symbol{
    font-weight: 100;
}
</style>