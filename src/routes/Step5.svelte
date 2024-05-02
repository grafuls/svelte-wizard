<script>
  let formData = {
    nombre: '',
    email: '',
    compania: '',
    telefono: ''
  }
</script>



<label class="label">
    <h2>Nombre</h2>
	<input class="input variant-form-material" bind:value={formData.nombre} type="text">
</label>
<label class="label">
    <span>Email</span>
    <input class="input variant-form-material" bind:value={formData.email} type="text">
</label>
<label class="label">
    <span>Compañia actual</span>
    <input class="input variant-form-material" bind:value={formData.compania} type="text">
</label>
<label class="label">
    <span>Telefono</span>
    <input class="input variant-form-material" bind:value={formData.telefono} type="text">
</label>