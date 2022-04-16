<script>
  export let icon;
  export let title;
  export let description;
</script>

<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bulma@0.9.3/css/bulma.min.css" />
<div class="card">
  <div class="card-content">
    <div class="media">
      <div class="media-left">
        <figure class="image is-48x48">
          <img src={icon} alt="Placeholder" />
        </figure>
      </div>
      <div class="media-content">
        <p class="title is-4">{title}</p>
      </div>
    </div>

    <div class="content">{description}.</div>
  </div>
</div>

<style>
  .card {
    margin: 20px;
    width: 300px;
  }
</style>
