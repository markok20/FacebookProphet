# FacebookProphet

Forecasting time series using Facebook Prophet

Nokian tuleva kurssikehitys: Kuinka tehdä täydellinen ennustusmalli Facebook Prophetilla?

Miten osakekurssi kehittyy seuraavien viikkojen tai kuukausien aikana? Voidaanko osakkeen kurssikehityksestä nähdä kausittaista vaihtelua? Milloin päätöskurssi on historiadatan pohjalta maksimitasolla? Mikä päätöskurssi on 100 päivän päästä?

Näihin kysymyksiin hain vastauksia, kun ennustin Nokian osakekurssikehitystä historiadatan pohjalta. Menetelmänä on Facebook Prophet, joka soveltuu eri tyyppisten aikasarjadatojen ennustamiseen, mihin liittyy kausittaista vaihtelua. Ennustusmenetelmän on kehittänyt nimenmukaisesti Facebookin Data Science -tiimi.

Aineistona oli Nokian päätöskurssi (USD) 1.1.2015-31.3.2021. Kyseiseen historiadataan pääsee muun muassa osoitteesta:

https://finance.yahoo.com/quote/NOK/history?p=NOK

Aineistoa käsittelin Pythonilla, jonne toin asianmukaiset kirjastot muun muassa Pandaksen ja Matplotlibin sekä Prophetin. Artikkelin lopussa on linkki Python-koodiin.

DISCLAIMER: Tärkeää on se, että tämän kirjoituksen tehtävänä on olla opetusluonteinen, tarkoituksena ei ole antaa sijoitusneuvoja eikä kannustaa ostamaan osakkeita.

Yksi Facebook Prophetin eduista on se, että se visualisoi päivittäiset, viikoittaiset ja vuosittaiset vaihtelut sekä tarvittaessa eliminoi lomavaikutukset. Lyhyesti Prophetin matemaattinen kaava on seuraavanlainen:

y(t) = g(t) + s(t) + h(t) + e(t)
g(t) = trendi
s(t) = kausittaiset vaihtelut (viikko, kuukausi, vuosi)
h(t) = lomavaikutukset
e(t) = virhe/error/noise

Prophet-malli on sovitettavissa dataan nopeasti huolimatta havaintojen määrästä, eikä se vaadi suuressa määrin datan esikäsittelyä. Malli huomioi myös puuttuvat havainnot ja luotettavuusrajat. Tässä kirjoituksessa näytän, miten hyödynnän mallia Nokian osakekurssihinnan ennustamisessa.

Kuvataan aluksi tilastolliset perustunnusarvot ajanjaksolta 1.1.2015-31.3.2021 eli keskiarvo, mediaani, minimi, maksimi ja keskihajonta. Näyttää siltä, että viimeisten kuuden vuoden aikana osakkeen päätöskurssin keskiarvo on ollut noin 5,47 USD, maksimi 8,3 USD ja minimi 2,42 USD.

Visualisoidaan seuraavaksi päätöskurssikehitys. Viimeisen vuoden kehityksen osalta huomaan, että kurssikehitys kääntyi jyrkkään laskuun koronapandemian puhkeamisen takia maaliskuussa 2020 ja kääntyi jyrkkään nousuun sosiaalisen median keskustelujen myötä tammikuussa 2021.

Rakennetaan seuraavaksi ennustusmalli. Käytämme mallissa ainoastaan päivämäärää ja päätöskurssia eli ds = päivämäärä ja y = päätöskurssi kunakin päivänä. En jaa dataa opetus- ja testidataan, vaan sovitan mallia koko dataan ja käsken ennustamaan tulevan kehityksen tämän pohjalta.

Malli käyttää sovittamiseen toteutunutta kehitystä (mustat pisteet) ja ennustaa kehitystä luotettavuusrajoineen. Sadan päivän ennustuksen mukaan Nokian päätöskurssi on noin 4,3 USD heinäkuun alussa. 

Kuvataan seuraavaksi trendi eli viikottainen, kausittainen, vuosittainen ja päivittäinen vaihtelu. Trendin perusteella nähdään, että osakekurssi yleensä nousee maksimitasolleen elokuun alussa ja keskiviikkoisin. Lisäksi nähdään kurssikehitys tulevaisuudessa luotettavuusrajoineen.
