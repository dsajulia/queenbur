<script>
  import { tick } from 'svelte';
  import MessageBubble from './MessageBubble.svelte';
  import TypingIndicator from './TypingIndicator.svelte';

  // No Svelte 5, as props e os callbacks de eventos são recebidos via $props()
  let { 
    messages = [], 
    isTyping = false, 
    onselectOption 
  } = $props();

  let container = $state();

  async function scrollToBottom() {
    await tick();
    if (container) {
      container.scrollTop = container.scrollHeight;
    }
  }
  $effect(() => {
    messages;
    isTyping;
    scrollToBottom();
  });
/** @param {string} option */
  function handleOptionClick (option) {
    if (onselectOption) {
      onselectOption(option);
    }
  }
</script>

<div class="message-container" bind:this={container}>
  {#each messages as msg (msg.id)}
    <div class="message-group {msg.sender}">
      <MessageBubble
        text={msg.text}
        sender={msg.sender}
        author={msg.author}
        time={msg.time}
      />

      <!-- Opções do cardápio do Queenbur (Chips) -->
      {#if msg.options && msg.options.length > 0}
        <div class="options-group">
          {#each msg.options as option}
            <button
              type="button"
              class="chip-btn"
              onclick={() => handleOptionClick(option)}
            >
              {option}
            </button>
          {/each}
        </div>
      {/if}
    </div>
  {/each}

  {#if isTyping}
    <div class="typing-wrapper">
      <TypingIndicator />
    </div>
  {/if}
</div>

<style>
  .message-container {
    flex: 1;
    padding: 16px;
    overflow-y: auto;
    background-color: #fafafa;
    display: flex;
    flex-direction: column;
    gap: 12px;
  }

  .message-group {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  .message-group.user {
    align-items: flex-end;
  }

  .message-group.bot {
    align-items: flex-start;
  }

  .options-group {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 6px;
    max-width: 85%;
  }

  .chip-btn {
    background: #fff3e0;
    border: 1px solid #ffe0b2;
    color: #e67e22;
    padding: 6px 12px;
    border-radius: 16px;
    font-size: 12px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.2s, transform 0.1s;
  }

  .chip-btn:hover {
    background: #ffe0b2;
    transform: translateY(-1px);
  }

  .chip-btn:active {
    transform: translateY(0);
  }

  .typing-wrapper {
    align-self: flex-start;
    margin-top: 2px;
  }
</style>
