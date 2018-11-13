<template>
    <div>
        <h1>Counter!</h1>

        <p>This is a simple example of a Vue.js component & Vuex</p>

        <p>
            Current count (Vuex): <strong>{{ currentCount }}</strong>
        </p>
        <p>
            Auto count: <strong>{{ autoCount }}</strong>
        </p>

        <p>
            Total count: <strong>{{ totalCounter }}</strong>
        </p>

        <button type="button" class="btn btn-primary" @click="incrementCounter()">Increment</button>
        <button type="button" class="btn btn-secondary" @click="resetCounter()">Reset</button>
        <button type="button" class="btn btn-primary" @click="toggleAutoCounter()">Toggle Auto Counter</button>

        <input type="checkbox" id="checkbox" v-model="checked">
        <label for="checkbox">{{ checked }}</label>

        <a asp-controller="Home" asp-action="Index" class="btn btn-info navbar-btn">Go Home</a>
    </div>
</template>

<script>
    export default
    {
        data () {
        return {
            autoCount: 0,
            currentCount: 0,
            autoCounterEnabled: true,
            checked: false
        }
        },

        computed:
        {
            totalCounter: function ()
            {
                return this.autoCount + this.currentCount;
            }
        },

        methods:
        {
            incrementCounter: function ()
            {
                this.currentCount += 1;
            },

            resetCounter: function ()
            {
                this.currentCount = 0;
                this.autoCount = 0;
            },

            toggleAutoCounter: function ()
            {
                this.autoCounterEnabled = !this.autoCounterEnabled;
            }
        },

        created()
        {
            setInterval(() =>
            {
                if (this.autoCounterEnabled) {
                    this.autoCount += 1
                }
            }, 1000);
        }
    }
</script>

<style>
</style>
