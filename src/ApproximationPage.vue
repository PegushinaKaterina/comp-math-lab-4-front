<template>
    <div class="app">
        <div class="header">
            <h2>Аппроксимация функции</h2>
        </div>
        <div class="main">
            <div class="userInput">
                <div class="forms appElement">
                    <approximation-form class="form"
                                        @solve="solve"
                                        @reset="reset"
                                        @error="error"
                    />
                </div>
                <div v-if="errors.length > 0" class="result appElement">
                    <div v-for="message in errors">
                        {{message}}
                    </div>
                </div>
                <div v-else class="result appElement">
                </div>
            </div>
            <div class="plots">
                <div class="plot">
                    <plot :fnProp="functions" :leftProp="left" :rightProp="right" :bottomProp="bottom" :topProp="top" :pointsProp="points"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import ApproximationForm from "@/components/ApproximationForm.vue";
import Plot from "@/components/Plot.vue";

export default {
    components: {
        Plot,
        ApproximationForm
    },
    name: "App",
    data() {
        return {
            functions: ['x'],
            left: -5,
            right: 5,
            bottom: -5,
            top: 5,
            points: [],
            errors: [],
        };
    },
    methods: {
        solve(data, left, right, bottom, top, points) {
            this.left = left
            this.right = right
            this.bottom = bottom
            this.top = top
            this.points = points
            this.functions = data
            this.errors = []
            console.log(data)
        },
        reset() {
            this.fn = ""
            this.left = -5
            this.right = 5
            this.bottom = -5
            this.top = 5
            this.points = []
            this.errors = []
        },
        error(errors) {
            this.errors = errors;
            console.log(errors)
        },
    },
};
</script>


<style scoped>
*:global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    border-radius: 7px;
    background-color: #d7d4c9;
    font-family: "Courier New";
    font-weight: bolder;
    color: black;
}

.app {
    width: 100%;
    padding: var(--padding-size);
    display: flex;
    flex-direction: column;
    box-sizing: border-box;
    --text-size: 15px;
    --text-size-header: 40px;
    --padding-size: 5px;
    --button-size: 110px;
    --button-padding-size: 5px;
    --element-form-text-size: 15px;
}

.main {
    font-size: var(--text-size);
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    margin: 20px;
    padding: 20px;
}

.header {
    width: 100%;
    text-align: center;
    font-size: var(--text-size-header);
    margin: 50px 0px 20px 0px;
}

.result {
    width: 400px;
    display: flex;
    flex-direction: row;
}

.appElement {
    height: 650px;
    margin: 20px;
    padding: 20px;
    border: 1.5px solid black;
    display: flex;
    flex-direction: column;
}

.forms {
    width: 600px;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    --button-size: 130px;
    --button-padding-size: 10px;
    --element-form-text-size: 15px;
}
.userInput {
    display: flex;
    flex-direction: row;
    justify-content: space-evenly;
}
</style>

