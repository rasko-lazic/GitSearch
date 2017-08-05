<template>
    <div>
        <div class="container search-input-container">
            <div class="row">
                <div class="col-md-6 col-md-offset-3">
                    <form @submit.prevent="startSearch">
                        <div class="input-group">
                            <input type="text" class="form-control" placeholder="Search..." v-model="searchQuery">
                        <span class="input-group-btn">
                            <button class="btn btn-secondary btn-search" type="submit">
                                Start
                            </button>
                        </span>
                        </div>
                    </form>
                </div>
            </div>
        </div>

        <div class="container saved-results-container">

        </div>
    </div>
</template>

<script>
    export default {
        name: 'home',

        data () {
            return {
                searchQuery: ''
            }
        },

        methods: {
            startSearch() {
                if(this.searchQuery.length > 0) {
                    this.$router.push('search/' + this.searchQuery + '/1');
                } else {
                    alert("Please don't leave the search filed empty");
                }
            }
        },

        created() {
            console.log('created');
        }
    }
</script>

<style scoped>
    .search-input-container {
        margin-top: 150px;
    }

    .btn-search {
        min-width: 75px;
    }

    .glyphicon-refresh-animate {
        -animation: spin .7s infinite linear;
        -webkit-animation: spin2 .7s infinite linear;
    }

    @-webkit-keyframes spin2 {
        from { -webkit-transform: rotate(0deg);}
        to { -webkit-transform: rotate(360deg);}
    }

    @keyframes spin {
        from { transform: scale(1) rotate(0deg);}
        to { transform: scale(1) rotate(360deg);}
    }
</style>