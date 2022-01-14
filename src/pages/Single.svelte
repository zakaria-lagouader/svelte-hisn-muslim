<script>
	import { useParams } from "svelte-navigator";
    import { onMount } from "svelte";
    let data = [];
    let title = ""
    const params = useParams();

    onMount(() => {
        fetch("/husn_en.json")
            .then(res => res.json())
            .then(({English}) => {
                data = English.find(i => i.ID == $params.id)
                title = data.TITLE;
                data = data.TEXT
                console.log(data);
            })
    })


</script>

<div class="container">
    <h5 class="mb-5">{title}</h5>
    {#if data.length > 0}
        {#each data as hadith}
            <div class="card mb-3">
                <div class="card-body">
                    <div class="text-right">
                        <h6 class="card-subtitle mb-2 text-muted">العربية</h6>
                        <p class="card-text">{hadith.ARABIC_TEXT}</p>
                    </div>
                <hr>
                <h6 class="card-subtitle mb-2 text-muted">English</h6>
                <p class="card-text">{hadith.TRANSLATED_TEXT}</p>
                </div>
            </div>
        {/each}
    {/if}

</div>