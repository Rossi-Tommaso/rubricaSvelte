<script>
    import { rubrica } from "../stores/rubrica"

    let surname = '';
    let name = '';
    let address = '';
    let phone = '';


    function save() {
        let contatto = {
            cognome: surname,
            nome: name,
            indirizzo: address,
            telefono: phone
        };

        $rubrica = [...$rubrica, contatto];
        console.log(rubrica)

        surname = '';
        name = '';
        address = '';
        phone = '';
    }

    function find() {
        let trovato = false;
        $rubrica.forEach((element, index) => {
            if ((surname && surname.toLocaleLowerCase() === element.cognome.toLocaleLowerCase()) || (phone && phone === element.telefono))
                surname = element.cognome;
                name = element.nome;
                address = element.indirizzo;
                phone = element.telefono;
                trovato = true;                      
        });
        if (!trovato)
            alert('Nessun contatto trovato')
        
    }
</script>

<input bind:value={surname} type="text" placeholder="Cognome" size="15" />
<input bind:value={name} type="text" placeholder="Nome" size="15" />
<input bind:value={address} type="text" placeholder="Indirizzo" size="30" />
<input bind:value={phone} type="text" placeholder="Telefono" size="10" />
<button on:click={find}>Cerca</button>
<button on:click={save}>Salva</button>
