<script lang="ts">
  export function action(a: number, b: number) {
    console.log(a, b);
    return "This shouldn't work";
  }
</script>

<p>Component with readonly function prop with incompatible signature</p>
