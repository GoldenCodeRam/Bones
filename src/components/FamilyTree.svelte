<script lang="ts">
  const firstLevel = [
    {
      name: "Médula espinal",
      secondLevel: [
        {
          name: "Segmentos cervicales",
          thirdLevel: [
            { name: "Cervical" },
            { name: "CervicoTráxico" },
            { name: "ToracoLumbar" },
            { name: "LumboSacro" },
          ],
        },
      ],
    },
  ];
</script>

<main>
  <div class="container">
    <p>Sistema Nervioso de los Cánidos 🐶</p>
    <div class="wrapper">
      <span class="label">Sistema nervioso</span>
      <div class="branch lv1">
        {#each firstLevel as { name, secondLevel }}
          <div class={firstLevel.length > 1 ? "entry" : "entry sole"}>
            <span class="label">{name}</span>
            {#if secondLevel.length > 0}
              <div class="branch lv2">
                {#each secondLevel as { name, thirdLevel }}
                  <div class={secondLevel.length > 1 ? "entry" : "entry sole"}>
                    <span class="label">{name}</span>
                    {#if thirdLevel.length > 0}
                      <div class="branch lv3">
                        {#each thirdLevel as { name }}
                          <div class={thirdLevel.length > 1 ? "entry" : "entry sole"}>
                            <span class="label">{name}</span>
                          </div>
                        {/each}
                      </div>
                    {/if}
                  </div>
                {/each}
              </div>
            {/if}
          </div>
        {/each}
      </div>
    </div>
  </div>
</main>

<style lang="scss">
  //------- {{ Variables }} -------//

  $white: #eee9dc;
  $bg: #2e6ba7;

  $horizontal-gutter: 100px;
  $border-radius: 10px;

  $entry-min-height: 60px;

  $label-width: 150px;
  $label-height: 30px;
  $label-border-radius: 5px;

  //------- {{ Styles }} -------//

  *,
  *:before,
  *:after {
    box-sizing: border-box;
  }

  main {
    width: 100%;
  }

  .container {
    display: flex;
    flex-direction: column;
    background: #FAFAFA;
    border-radius: 15px;
    padding: 1em 4em;
    overflow: auto;
  }

  .wrapper {
    display: inline-block;
    position: relative;
  }

  .branch {
    position: relative;
    margin-left: $horizontal-gutter + $label-width;
    max-width: $label-width;
    &:before {
      content: "";
      width: $horizontal-gutter / 2;
      border-top: 2px solid $white;
      position: absolute;
      left: -$horizontal-gutter;
      top: 50%;
      margin-top: 1px;
    }
  }

  .entry {
    position: relative;
    min-height: $entry-min-height;
    &:before {
      content: "";
      height: 100%;
      border-left: 2px solid $white;
      position: absolute;
      left: -($horizontal-gutter / 2);
    }
    &:after {
      content: "";
      width: $horizontal-gutter / 2;
      border-top: 2px solid $white;
      position: absolute;
      left: -($horizontal-gutter / 2);
      top: 50%;
      margin-top: 1px;
    }
    &:first-child {
      &:before {
        width: $border-radius;
        height: 50%;
        top: 50%;
        margin-top: 2px;
        border-radius: $border-radius 0 0 0;
      }
      &:after {
        height: $border-radius;
        border-radius: $border-radius 0 0 0;
      }
    }
    &:last-child {
      &:before {
        width: $border-radius;
        height: 50%;
        border-radius: 0 0 0 $border-radius;
      }
      &:after {
        height: $border-radius;
        border-top: none;
        border-bottom: 2px solid $white;
        border-radius: 0 0 0 $border-radius;
        margin-top: -$border-radius + 1px;
      }
    }
    &.sole {
      &:before {
        display: none;
      }
      &:after {
        width: $horizontal-gutter / 2;
        height: 0;
        margin-top: 1px;
        border-radius: 0;
      }
    }
  }

  .label {
    display: block;
    min-width: $label-width;
    padding: 5px 10px;
    line-height: $label-height - 5px * 2;
    text-align: center;
    border-radius: $label-border-radius;
    position: absolute;
    left: 0;
    top: 50%;
    margin-top: -($label-height / 2);

    background: #fafafa;
    border: 1px solid #b3b3b3;
    box-shadow: 0px 2px 0px #b3b3b3;

    &:hover {
      background: #f3f3f3;
    }
    &:active {
      transform: translateY(2px);
      box-shadow: none;
    }
  }
</style>
