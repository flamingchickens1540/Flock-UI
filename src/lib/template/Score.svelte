<script lang="ts">
</script>

<style>
    #minus {
        background-color: #ff3333;
    }

    #add {
        background-color: lime;
    }

    #left {
        border-top-left-radius: 4px;
        border-bottom-left-radius: 4px;
    }

    #right {
        border-top-right-radius: 4px;
        border-bottom-right-radius: 4px;
    }

    .edge {
        border-width: 2px;
        border-radius: 4px;
        border-style: solid;

        margin:0px;
        padding: 4px;
    }

    .score {
        background-color: #efdcdc;

        margin:0px;
        border-style: solid;
        border-width: 0px;
        padding: 0px;

        width: 33%;
    }

    #middle {
        padding: auto;
    }

    #holder {
        display:flex; 
        flex-direction:row;
    }
</style>

<div id="holder">
    <button class="score" id="left"><div class="edge" id="minus">+1</div></button>
    <button style="" class="score" id="middle">-1</button>
    <button class="score" id="right"><div class="edge" id="add">+1</div></button>
</div>