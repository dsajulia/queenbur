<script>
  // Declaração de props no Svelte 5
  let { 
    text = "", 
    time = "", 
    sender = "other", 
    author = "" 
  } = $props();
</script>

<div class="message-wrapper {sender}">
  <div class="bubble">
    {#if sender === 'other' && author}
      <span class="author">{author}</span>
    {/if}
    <p class="text">{text}</p>
    <span class="time">{time}</span>
  </div>
</div>

<style>
  .message-wrapper {
    display: flex;
    width: 100%;
    margin-bottom: 8px;
  }

  .message-wrapper.user {
    justify-content: flex-end;
  }

  .message-wrapper.bot,
  .message-wrapper.other {
    justify-content: flex-start;
  }

  .bubble {
    max-width: 75%;
    padding: 10px 14px;
    border-radius: 16px;
    word-break: break-word;
  }

  .user .bubble {
    background-color: #e67e22;
    color: #ffffff;
    border-bottom-right-radius: 2px;
  }

  .bot .bubble,
  .other .bubble {
    background-color: #ffffff;
    color: #2c3e50;
    border-bottom-left-radius: 2px;
    border: 1px solid #e2e8f0;
  }

  .author {
    display: block;
    font-size: 11px;
    font-weight: bold;
    color: #d35400;
    margin-bottom: 2px;
  }

  .text {
    margin: 0;
    font-size: 14px;
    line-height: 1.4;
    white-space: pre-line;
  }

  .time {
    display: block;
    font-size: 10px;
    margin-top: 4px;
    text-align: right;
    opacity: 0.7;
  }
</style>
