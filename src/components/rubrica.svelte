<script>
    import { rubrica } from "../stores/rubrica"

    let element = '';

    function remove(index) {
        $rubrica = $rubrica.filter((_, i) => i !== index);
    }

    $: console.log($rubrica)
</script>

{#if $rubrica.length > 0}
    <div class="rubrica-list">
        {#each $rubrica as contatto, index}
            <div class="rubrica-item">
                <div class="contact-info">
                    <div class="field">
                        <span class="label">Cognome:</span>
                        <span class="value">{contatto.cognome}</span>
                    </div>
                    <div class="field">
                        <span class="label">Nome:</span>
                        <span class="value">{contatto.nome}</span>
                    </div>
                    <div class="field">
                        <span class="label">Indirizzo:</span>
                        <span class="value">{contatto.indirizzo}</span>
                    </div>
                    <div class="field">
                        <span class="label">Telefono:</span>
                        <span class="value">{contatto.telefono}</span>
                    </div>
                </div>
                <button 
                    bind:this={element} 
                    on:click={() => remove(index)}
                    class="remove-btn"
                >
                    Rimuovi
                </button>
            </div>
        {/each}
    </div>
{/if}

<style>
    .rubrica-list {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-content: space-around;
        justify-content: space-evenly;
        max-width: 900px;
        margin: 0 auto;
        padding: 1rem;
    }

    .rubrica-item {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1.25rem;
        background-color: #ffffff;
        border-radius: 8px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
        transition: transform 0.2s ease, box-shadow 0.2s ease;
    }

    .rubrica-item:hover {
        transform: translateY(-2px);
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
    }

    .contact-info {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1rem;
        flex-grow: 1;
    }

    .field {
        display: flex;
        flex-direction: column;
        gap: 0.25rem;
    }

    .label {
        font-weight: 600;
        color: #666;
        font-size: 0.875rem;
    }

    .value {
        color: #333;
        font-size: 1rem;
    }

    .remove-btn {
        padding: 0.5rem 1rem;
        background-color: #dc3545;
        color: white;
        border: none;
        border-radius: 6px;
        cursor: pointer;
        font-weight: 500;
        transition: background-color 0.2s ease;
        margin-left: 1rem;
        min-width: 100px;
    }

    .remove-btn:hover {
        background-color: #c82333;
    }

    .remove-btn:active {
        transform: scale(0.98);
    }

    @media (max-width: 768px) {
        .rubrica-item {
            flex-direction: column;
            align-items: stretch;
        }

        .contact-info {
            grid-template-columns: 1fr;
        }

        .remove-btn {
            margin-left: 0;
            margin-top: 1rem;
            width: 100%;
        }
    }
</style>