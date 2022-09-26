<script>
    import { createEventDispatcher } from "svelte";

    let text = ''
    let rating = 0;
    const dispatch = createEventDispatcher()

    const handleFormSubmit = (e) => {
        e.preventDefault()
        dispatch('add-feedback', { text, rating})
        text = ''
        rating = 0;
    }
</script>

<form on:submit={handleFormSubmit}>
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
        <button disabled={ text =='' || rating === 0}>Send</button>
    
</form>

<style>
    form {
        max-width: 200px;
        margin: 0 auto;
        padding: 20px;
        background-color: orange;
        border-radius: 10px
    }
    .input-group {
        margin: 1em 0;
    }
    .radio-group label {
        display: block;
        margin: 2.5px;
    }
    button {
        display: block;
        margin: 1em auto 0 auto;
    }
</style>