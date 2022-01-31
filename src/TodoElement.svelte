<script lang="ts">
    function del() {
        document.getElementById("todoelem").remove()
    } 
    export let value: string
</script>

<style>
    
    #todoelem {
        height : 50px;
        font-family: D2Coding;
        font-size: 25px;
        font-weight: 400;
        margin: 1rem;
    }
    #todoelem input {
        width: 20px;
        height: 20px;
    }
    #value {
        font-size: 30px;
    }
    #delete {
        text-align: right;
        margin : 0px;
        display: none;
        border-radius: 7px;

        background-color: rgb(255, 50, 50);
        height : 50px;
    }
    #todoelem:hover #delete {
        display: initial;
    }

    #cb:checked + #value {
        text-decoration: line-through;
        color: gray;
    }
</style>

<link href="http://cdn.jsdelivr.net/gh/joungkyun/font-d2coding/d2coding.css" rel="stylesheet" type="text/css">
<div id="todoelem">
    <input id="cb" type="checkbox">
    <span id="value">{value}</span>
    <button id="delete" on:click="{del}">
        <img src="data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij48cGF0aCBkPSJNMyA2djE4aDE4di0xOGgtMTh6bTUgMTRjMCAuNTUyLS40NDggMS0xIDFzLTEtLjQ0OC0xLTF2LTEwYzAtLjU1Mi40NDgtMSAxLTFzMSAuNDQ4IDEgMXYxMHptNSAwYzAgLjU1Mi0uNDQ4IDEtMSAxcy0xLS40NDgtMS0xdi0xMGMwLS41NTIuNDQ4LTEgMS0xczEgLjQ0OCAxIDF2MTB6bTUgMGMwIC41NTItLjQ0OCAxLTEgMXMtMS0uNDQ4LTEtMXYtMTBjMC0uNTUyLjQ0OC0xIDEtMXMxIC40NDggMSAxdjEwem00LTE4djJoLTIwdi0yaDUuNzExYy45IDAgMS42MzEtMS4wOTkgMS42MzEtMmg1LjMxNWMwIC45MDEuNzMgMiAxLjYzMSAyaDUuNzEyeiIvPjwvc3ZnPg==">
    </button>
</div>