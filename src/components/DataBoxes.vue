<template>
    <div class="main-div">
        
        <!-- BOX 1 -->
        <div class="box-1">
            <h3 class="box-title">
                Cases
            </h3>

            <div class="box-font">
                <span class="info-title">Today: </span>
                {{ numberWithCommas(stats.slice(-1)[0].Active) }}
            </div>

            <div class="box-font">
                <span class="info-title">Total: </span>
                {{ numberWithCommas(stats.slice(-1)[0].Confirmed) }}
            </div>
        </div>

        <!-- BOX 2 -->
        <div class="box-2">
            <h3 class="box-title">
                Survival
            </h3>

            <div class="box-font">
                <span class="info-title">Total Deaths: </span>
                {{ numberWithCommas(stats.slice(-1)[0].Deaths) }}
            </div>

            <div class="box-font">
                <span class="info-title">Total Recovery: </span>
                {{ numberWithCommas(stats.slice(-1)[0].Recovered) }}
            </div>
        </div>
        
    </div>

    <div class="survival-div">

        <h3 class="survival-title">Survival Rates</h3>

        <div class="rate-div">

            <div class="death-percentage">
                Death Percentage: 
                <span class="num-span">
                {{ Math.round(((stats.slice(-1)[0].Deaths)/(stats.slice(-1)[0].Deaths + stats.slice(-1)[0].Recovered) * 100) * 100) /100 }}%
                </span>
            </div>

            <div class="recovery-percentage">
                Recovery Percentage: 
                <span class="num-span">
                    {{ Math.round(((stats.slice(-1)[0].Recovered)/(stats.slice(-1)[0].Deaths + stats.slice(-1)[0].Recovered) * 100) * 100) /100 }}%
                </span>
            </div>

        </div>

    </div>

    <div class="survival-div">

        <h3 class="survival-title">Recent Comparison</h3>

        <div class="rate-div">

            <div class="death-percentage">
                Cases Yesterday: 
                <span class="num-span">
                    {{ numberWithCommas(stats.slice(-2)[0].Active) }}
                </span>
            </div>

            <div class="recovery-percentage">
                Cases Last Week:
                <span class="num-span">
                    {{ numberWithCommas(stats.slice(-8)[0].Active) }}
                </span>
            </div>

        </div>

        <div class="rate-div">

            <div class="death-percentage">
                Cases Last Month: 
                <span class="num-span">
                    {{ numberWithCommas(stats.slice(-31)[0].Active) }}
                </span>
            </div>

            <div class="recovery-percentage">
                Cases Last Year:
                <span class="num-span">
                    {{ numberWithCommas(stats.slice(-366)[0].Active) }}
                </span>
            </div>

        </div>

    </div>

    <hr>

    <footer class="footer">
        Hilal G. | Current Year: {{ new Date().getFullYear() }}
    </footer>
</template>

<script>

export default {
    name: 'DataBoxes',
    props: ['stats'],
    methods: {
        numberWithCommas(x) {
            return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
}
</script>

<style>

.main-div {
    display: flex;
    justify-content: center;
    align-items: center;
}

.box-1 {
    display: inline-block;
    background-color: #ffc9ab;
    padding: 15px;
    border-radius: 10px;
    width: 550px;
    margin-right: 5px;
}

.box-2 {
    display: inline-block;
    background-color: #ffb084;
    padding: 15px;
    border-radius: 10px;
    width: 550px;
    margin-left: 5px;
}

.box-title {
    display: flex;
    justify-content: center;
    align-items: center;
    font-weight: bold;
    font-size: 24px;
    padding: 5px;
}

.info-title {
    font-weight: bold;
    padding: 5px;
}

.box-font {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 20px;
}

.rate-div {
    display: flex;
    justify-content: center;
    align-items: center;
    padding-bottom: 15px;
}

.survival-title {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 30px;
    font-weight: bold;
    padding: 10px;
}

.death-percentage {
    display: inline-block;
    margin-right: 15px;
    font-size: 30px;
}

.recovery-percentage {
    display: inline-block;
    margin-right: 15px;
    font-size: 30px;
}

.survival-div {
    padding: 10px;
}

.num-span {
    font-size: 40px;
}

.footer {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 25px;
    font-size: 20px;
    color: #e61b009d;
}

hr {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-left: 50px;
    margin-right: 50px;
}

</style>
