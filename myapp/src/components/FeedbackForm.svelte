<script>
    import { createEventDispatcher } from "svelte";

    let text = ''
    let rating = 0;
    const dispatch = createEventDispatcher()
    export let currentItem

    const handleFormSubmit = () => {
        if(currentItem.rating === undefined) {
            dispatch('add-feedback', { text, rating})
        } else {
            dispatch('add-feedback', { text, rating, currentItem})
        }
           
        text = ''
        rating = 0
        currentItem={}
    }

    $: buttonLabel = currentItem.text === undefined ? 'Add' : 'Update'

    $: {
        if(currentItem.text) {
            if(text!=currentItem.text && rating!=currentItem.rating) {
        text = currentItem.text
        rating = currentItem.rating
        }
        }
    }

    function clearForm() {
        text = ''
        rating = 0
        currentItem={}
    }
</script>

<h2>{buttonLabel} Review</h2>
<form on:submit|preventDefault={handleFormSubmit}>
    <div class="input-group">
        <input type="text" bind:value={text} placeholder="Give us some feedback ">
    </div>
    <div class="radio-group">
        <label>
            <input type=radio bind:group={rating} name="rating" value={1}>
            One rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={2}>
            Two rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={3}>
            Three rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={4}>
            Four rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={5}>
            Five rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={6}>
            Six rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={7}>
            Seven rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={8}>
            Eight rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={9}>
            Nine rating
        </label>
        <label>
            <input type=radio bind:group={rating} name="rating" value={10}>
            Ten rating
        </label>

    </div>
        <div class='buttonDiv'>
        <button disabled={ text === '' || rating === 0}>{buttonLabel}</button>
        <button on:click={clearForm}>Clear</button>
    </div>
</form>

<style>
    form {
        max-width: 800px;
        margin: 0 auto;
        padding: 20px;
        background-color: orange;
        border-radius: 10px
    }
    .input-group {
        margin: 1em 0;
    }
    .input-group input{ 
        width: 100%;
    }
    .radio-group label {
        display: block;
        margin: 2.5px;
    }
    button {
        display: block;
        margin: 1em auto 0 auto;
    }
    h2{
        color: white;
        text-align: center;
    }
</style>