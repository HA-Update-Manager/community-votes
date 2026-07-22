# community-votes

Een gedeeld, git-gebaseerd stemsysteem: is een specifieke update van een
Home Assistant-integratie, apparaat-firmware, app, of Home Assistant zelf
**probleemloos** of **problematisch** gebleken? Gebouwd voor
[ha-update-manager](https://github.com/HA-Update-Manager/ha-update-manager),
maar bruikbaar door iedereen.

**Belangrijk: dit is een verzamelde mening, geen garantie.** Een "probleemloos"-
oordeel betekent dat de mensen die tot nu toe stemden geen problemen
tegenkwamen, niet dat een update voor jouw specifieke situatie ook
probleemloos zal zijn. Wees extra voorzichtig bij veiligheidsgevoelige
apparaten (sloten, alarmen, rookmelders): een community-oordeel vervangt geen
eigen inschatting.

"Probleemloos"/"problematisch" gaat over of een update werkt zoals verwacht
(geen bugs, geen gemiste minimale HA-versie, geen per ongeluk gepushte
dev-build, geen onaangekondigde breaking change), niet over
beveiliging/veiligheid in bredere zin.

## Hoe stemmen

Open een nieuwe issue via het "Stem uitbrengen"-formulier
([direct hier](../../issues/new?template=vote.yml)). Vul precies de velden in
die bij jouw gekozen categorie horen. Een GitHub Action verwerkt je stem
automatisch: het bijbehorende bestand verschijnt in `votes/`, en de issue
sluit met een bevestiging.

Geen account-koppeling nodig buiten een gewone GitHub-login: dit repo gebruikt
geen fork, geen aparte app-installatie aan jouw kant.

Je kunt eenmaal stemmen per persoon per exacte versie. Een tweede stem op
dezelfde versie wordt genegeerd, niet overschreven.

## Lezen

Alle bestanden in `votes/` zijn gewone, publieke JSON-bestanden, direct te
lezen via `raw.githubusercontent.com`, zonder account of API-rate-limit. Zie
`votes/README.md` voor de padstructuur.

## Moderatie

`moderation/banned-users.json` bevat GitHub-gebruikersnamen waarvan stemmen
niet meer verwerkt worden. Alleen door de organisatie-eigenaren aan te passen,
buiten de gewone stem-flow om. Meld misbruik via een comment op de
betreffende stem-issue (voordat die automatisch sluit) of een nieuwe issue
tegen dit repo.

## Instellingen

`config/site.json` bevat het quorum (minimum aantal probleemloos-stemmen
voordat een update als "geschikt voor automatisch installeren" geldt). Zie
`ha-update-manager`'s eigen `FUTURE.md` voor de volledige achtergrond van deze
eis (100% probleemloos, plus quorum).

## Toon

Dit is een verzameling meningen van gebruikers, geen rechterlijk oordeel over
een project of maker. Hou het bij het melden van een probleem zo feitelijk en
behulpzaam mogelijk.
