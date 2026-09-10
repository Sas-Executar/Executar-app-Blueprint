# Asset Contract Template

Todo asset visual (imagem, vídeo, ilustração) do produto EXECUTAR deve
possuir um Asset Contract com os campos abaixo.

```yaml
ASSET_ID:
type:              # image | video | illustration | icon
usage:             # onde é usado (ex.: hero de PAGE_ID)
subject:
message:
style:
composition:
ratio:
responsive_crop: []
safe_area:
alt_text:
caption:
rights:            # licenciamento/direitos de uso
source:            # referência a 99-SOURCES/provenance quando aplicável
status:            # DRAFT | APPROVED | PUBLISHED
```

Nenhum campo deve ser preenchido com valor inventado — usar `TBD`/`GAP`
onde a informação ainda não existe.
