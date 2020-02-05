# Tilastollinen tietosuoja

Tilastollisen tietosuojan englanti-suomi -sanakirja | 
Statistical Disclosure Control English-Finnish Dictionary

*"The purpose of Statistical Disclosure Control (SDC) for microdata is to
prevent confidential information from being linked to specific
respondents when releasing a microdata file. SDC seeks to optimise the
trade-off between the disclosure risk and the utility of the protected
released data"* [Hundepool 2012].


*Tilastollinen tietosuoja* on tekniikka, jolla pyritään
estämään julkaistavan yksikköaineiston luottamuksellisten muuttujien
liittäminen alkuperäisiin vastaajiin. TJH:n avulla pyritään etsimään
paras mahdollinen tasapaino julkaisuriskin ja julkaistun, mutta
suojeltavana pidettävän aineiston hyödyntämisen väliltä.
Tilastojulkisuutta käsittevää materiaalia ei juurikaan ole suomeksi.
Tästä syystä nimikkeistökään ei ole vakiintunut. Nimeä
**tilastojulkisuus** käytetään jatkossa perinteisen ja vakiintuneen
**tilastosalaisuus** termin vastinparina.

Tilastojulkisuus pyrkii julkistamaan aineistoa mahdollisimman paljon
ilman, että luottamukselliset yksikkötiedot varantuvat. Tilastosalaisuus
taas lähtee ajatuksesta, että aineisto kerätään ensisijaisesti vain
tilastointia varten ilman, että sitä koskaan käytetään toissijaisiin
tarkoituksiin tai yhdistetään muihin aineistoihin.

[**Tilastollisen tietosuojan englanti-suomi -sanasto**](sdc_en-fi.md)

Katso myös: [Aalto-yliopiston tilastotieteen sanasto
](https://math.aalto.fi/opetus/sovtoda/sanastot/en2fi.html)


### Julkistusriskin mittaaminen

Muuttujat voidaan jaotellan tunnisteellisuuden mukaan neljään luokkaan:

1. **tunnisteet** (eli yksikäsitteiset ja suorat tunnisteet); identifiers
2. **osatunnisteet** (tai epäsuorat tunnisteet); quasi-identifiers
3. **luottamukselliset muuttujat** (tai arkaluonteiset muuttujat);
   confidential or sensitive variables
4. **luonteeltaan julkiset muuttujat** (tai julkisluonteiset muuttujat);
   (non-confidential variables)

Muuttujan luonne riippuu yhteiskunnasta yleisestä julkisuuskäsityksestä.
Tämä on toisinaan kirjattu myös lakiin. [Eurooppalaisen tietosuoja-asetuksen
](https://eur-lex.europa.eu/legal-content/FI/TXT/?uri=CELEX%3A32016R0679) 
9. artiklassa todetaan

> **Erityisiä henkilötietoryhmiä koskeva käsittely**
> 
> 1. Sellaisten henkilötietojen käsittely, joista ilmenee rotu tai etninen
> alkuperä, poliittisia mielipiteitä, uskonnollinen tai filosofinen vakaumus tai
> ammattiliiton jäsenyys sekä geneettisten tai biometristen tietojen käsittely
> henkilön yksiselitteistä tunnistamista varten tai terveyttä koskevien tietojen
> taikka luonnollisen henkilön seksuaalista käyttäytymistä ja suuntautumista
> koskevien tietojen käsittely on kiellettyä.
> 
> 2. Edellä olevaa 1 kohtaa ei sovelleta, jos sovelletaan jotakin 
> seuraavista: (...)

jonka jälkeen luetellaan muun muassa *nimenomainen suostumus*, 
*velvoitteiden ja erityisten oikeuksien noudattaminen*,
*yleistä etua koskeva syy* ja *kansanterveyteen liittyvän yleinen etu*.
  

**Julkaisuriski** (disclosure risk), eli *uhka tilaston taustalla olevien
henkilöiden yksityisluonteisten tietojen paljastumisesta* riippuu
vastaanottajan käytössä olevista taustatiedoista. [Hundepool 2012, pp.
41] luettelee kolme tapausta:
  
1. Riski laskentaan pelkästään julkaistavan yksikköaineiston perusteella
2. Riski lasketaan taustalla olevan populaation ominaisuuksista. Lisäksi
   oletetaan, että tiedon mahdollisella väärinkäyttäjällä on kaikki
   tieto populaation tunnisteista ja osatunnisteista.
3. Riski laskentaan julkisesti saatavilla olevan lisäaineiston
   perusteella

Populaatio-oletuksen tapauksessa riski yksilöinnin palauttamisesta voidaan
määritellä todennäköisyydeksi

```math
r_k := \max_{i \in J} P (s [k] = p [i])
```

missä $k$ on yksilön tunniste otoksessa $s$ ja $J$ on koko populaation
$p$ tunnistejoukko (ns. indeksijoukko).

**Esimerkki.** Kokoomataulu (aggregate table) listaa kuvitteellisen
kunnan väestön vuonna 2019. Paikallisen vanhainkodin iäkkään
miesasiakkaan lattialta löytyy vasemmalla kädellä kirjoitettu paperi,
jossa on tallelokeron numero paikalliseen pankkiin. Todennäköisyys, että
tallokeron omistaja, $\mathrm{kuntalaiset}[k]$, arvataan oikein on $r_k
= 1/6$, mikäli käytössä on tilaston taustalla oleva yksikköaineisto
(lista kuntalaisista) nimineen.

| ikäryhmä | sukupuoli | kätisyys    | asukkaita |
|:---------|:----------|:------------|:---------:|
|   0 -14  |   mies    |   vasen     |   48      |
|   0 -14  |   mies    |   oikea     |   406     |
|   0 -14  |   nainen  |   vasen     |   43      |
|   0 -14  |   nainen  |   oikea     |   391     |
|   15-64  |   mies    |   vasen     |   175     |
|   15-64  |   mies    |   oikea     |   1565    |
|   15-64  |   nainen  |   vasen     |   169     |
|   15-64  |   nainen  |   oikea     |   1524    |
|   65-84  |   mies    |   vasen     |   52      |
|   65-84  |   mies    |   oikea     |   470     |
|   65-84  |   nainen  |   vasen     |   54      |
|   65-84  |   nainen  |   oikea     |   482     |
| **85-**  | **mies**  | **vasen**   |  **6**    | 
|   85-    |   mies    |   oikea     |   65      |
|   85-    |   nainen  |   vasen     |   7       |
|   85-    |   nainen  |   oikea     |   72      |

**Taulukko. (N=5525)** Kuvitteellinen tilasto suomalaisen, noin 
Ähtärin kokoisen kunnan väestöstä vuonna 2019.


### Lyhenteitä

**SDC** = Statistical Disclosure Control, tilastojulkisuuden hallinta (TJH)  
**ISI** = International Statistics Institute, Kansainvälinen tilastoinstituutti  
**ESS** = European Statistical System, Euroopan tilastojärjestelmä  
**HIPAA** = Health Insurance Portability and Accountability Act, amerikkalainen
  terveysvakuutusten siirrettävyys ja tilitysvastuulaki


### Viitteet

[Hundepool 2012] Statistical Disclosure Control. *Anco Hundepool Josep
Domingo‐Ferrer Luisa Franconi Sarah Giessing Eric Schulte Nordholt Keith
Spicer Peter‐Paul de Wolf*. First published:5 July 2012. John Wiley and
Sons. 

