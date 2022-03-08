nome : Gerar Dados
https://img.shields.io/badge/dynamic/json?url=<URL>&label=<LABEL>&query=<$.DATA.SUBDATA>&color=<COLOR>&prefix=<PREFIX>&suffix=<SUFFIX>

https://img.shields.io/badge/dynamic/xml?url=<URL>&label=<LABEL>&query=<//data/subdata>&color=<COLOR>&prefix=<PREFIX>&suffix=<SUFFIX>

https://img.shields.io/badge/dynamic/yaml?url=<URL>&label=<LABEL>&query=<$.DATA.SUBDATA>&color=<COLOR>&prefix=<PREFIX>&suffix=<SUFFIX>
em :
  schedule : # executa a cada 12 horas
-cron     : " * */12 * * * "
  workflow_dispatch :

empregos :
  construir :
    name : Jobs para atualizar dados
    run-on : ubuntu-latest
    passos :
      # Animação de cobra
      - usa : Platane/snk@master
        id : cobra-gif
        com :
          github_user_name : devemdobro
          svg_out_path : dist/github-contribution-grid-snake.svg

      - usa : crazy-max/ghaction-github-pages@v2.1.3
        com :
          target_branch : saída
          build_dir : dist
        ambiente :
          GITHUB_TOKEN : ${{ secrets.GITHUB_TOKEN }}
