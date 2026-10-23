<script>
  import logo from './logo.png'

  let { title = 'QueenBur', status = 'Online agora' } = $props()
</script>

<header>
  <img src={logo} alt="Logo da {title}" />
  <div>
    <h1>{title}</h1>
    <p><span class="dot"></span>{status}</p>
  </div>
</header>

<style>
  header {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 12px 16px;
    background: #f59e0b;
    color: white;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
  }

  img {
    width: 48px;
    height: 48px;
    border-radius: 50%;
    object-fit: cover;
    background: white;
  }

  h1 {
    margin: 0;
    font-size: 1.1rem;
  }

  p {
    margin: 0;
    display: flex;
    align-items: center;
    gap: 6px;
    font-size: 0.75rem;
  }

  .dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: #4ade80;
  }
</style>