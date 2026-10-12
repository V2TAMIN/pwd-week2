<script>
  let { data } = $props();
  let memo = $state('');

  $effect(() => {
    if (data.slug === 'memo') {
      memo = localStorage.getItem('memo') ?? '';
    }
  });

  function save() {
    localStorage.setItem('memo', memo);
    alert('저장 완료!');
  }
</script>

<h2>{data.item.title}</h2>
<p>{data.item.body}</p>

{#if data.slug === 'memo'}
  <label for="memo">메모 내용</label>

  <textarea
    id="memo"
    rows="6"
    bind:value={memo}
    class="card"
    style="width:100%"
  ></textarea>

  <button onclick={save}>메모 저장</button>
  <p style="opacity:0.6">브라우저 로컬에만 저장됩니다.</p>
{/if}