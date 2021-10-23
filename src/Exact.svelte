<script lang="ts">
  export function action(a: number): string | number {
    if (a >= 0.5) return "Large";
    return 0;
  }
</script>

<p>Component with readonly function prop with exact signature match</p>
