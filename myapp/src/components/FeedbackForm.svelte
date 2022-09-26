<script>
    let text = ''

    const handleInput = (e) => {
        text = e.target.value
    }
</script>

<form>
    <div class="input-group">
        <input type="text" on:input={handleInput} placeholder="Give us some feedback ">
        <button>Send</button>
    </div>
</form>

<style>
    form {
        max-width: 200px;
        margin: 0 auto;
        padding: 20px;
        background-color: orange;
        border-radius: 10px
    }
</style>