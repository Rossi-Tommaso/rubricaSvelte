<script>
    import Inputx from "../components/inputx.svelte";
    import Rubrica from "../components/rubrica.svelte";
</script>


<div class="container">
    <h1 class="main-title">Rubrica JS</h1>

    <div class="inputx">
        <Inputx />
    </div>

    <Rubrica />
</div>

<style>
    .container {
        font-family: 'Bebas Neue', sans-serif;
        width: 100dvw;
        height: 100dvh;
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    .main-title {
        text-align: center;
        font-size: 36px;
        margin-bottom: 20px;
    }
    .inputx {
        display: flex;
        gap: 10px;
        justify-content: center;
        margin-bottom: 20px;
    }

    .inputx input {
        padding: 5px;
        font-size: 16px;
    }

    .inputx button {
        padding: 5px 10px;
        background-color: #007bff;
        color: white;
        border: none;
    }

    .inputx button:hover {
        background-color: #0056b3;
    }
</style>
