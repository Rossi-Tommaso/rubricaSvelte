<script>
    import { element } from "svelte/internal";

    let surname = '';
    let name = '';
    let address = '';
    let phone = '';
    let contact = '';

    let rubrica = []

    function save() {
        let contatto = {
            cognome: surname,
            nome: name,
            indirizzo: address,
            telefono: phone
        };

        rubrica = [...rubrica, contatto];
        console.log(rubrica)
        surname = '';
        name = '';
        address = '';
        phone = '';
    }

    function find() {
    }

    function remove() {


    }

</script>


<div class="container">
    <h1 class="main-title">Rubrica JS</h1>

    <div class="inputx">
        <input bind:value={surname} type="text" placeholder="Cognome" size="15">
        <input bind:value={name} type="text" placeholder="Nome" size="15">
        <input bind:value={address} type="text" placeholder="Indirizzo" size="30">
        <input bind:value={phone} type="text" placeholder="Telefono" size="10">
        <button on:click={find}>Cerca</button>
        <button on:click={save}>Salva</button>
    </div>

    {#if rubrica.length > 0}
        <div class="rubrica-list">
            {#each rubrica as contatto}
                <div bind:this={contact} class="rubrica-item">
                    <div>Cognome: {contatto.cognome}</div>
                    <div>Nome: {contatto.nome}</div>
                    <div>Indirizzo: {contatto.indirizzo}</div>
                    <div>Telefono: {contatto.telefono}</div>  
                    <button on:click={remove}>Rimuovi</button>
                </div>       
            {/each}
        </div>
    {/if}
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

    .rubrica-list {
        display: grid;
        gap: 15px;
    }

    .rubrica-item {
        display: grid;
        grid-template-columns: repeat(4, 1fr) auto;
        gap: 10px;
        padding: 10px;
        background-color: #f9f9f9;
        border: 1px solid #ddd;
        border-radius: 5px;
    }

    .rubrica-item button {
        padding: 5px;
        background-color: #dc3545;
        color: white;
        border: none;
    }

    .rubrica-item button:hover {
        background-color: #c82333;
    }
</style>
