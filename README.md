# TuotekuvastoApp

**TuotekuvastoApp** on ASP.NET Core MVC -sovellus, joka näyttää tuotekatalogin JSON-tiedostosta haettujen tietojen pohjalta.
Sovellus sisältää tuotteiden näyttämisen Product-näkymässä sekä tuotekorttien ulkoasun ja hinnan muotoilun JavaScriptillä.

## Projektin rakenne

### Keskeiset osat

- **HomeController.cs**
  - Käsittelee tuotetietojen hakemisen ja välittää tiedot Product-näkymälle.
  - `Product()`-toimintometodi hakee tuotetiedot `GetProducts()`-metodista ja palauttaa Product-näkymän tuotetietojen kanssa.

- **Models/Product.cs**
  - Malli, joka edustaa yksittäistä tuotetta ja määrittää sen ominaisuudet (`Name`, `Price`, `Description`, `Image`).
  - Sisältää myös muotoiltuja ominaisuuksia (`FormattedName` ja `FormattedPrice`), jotka tekevät tiedoista käyttäjäystävällisempiä.

- **wwwroot/products.json**
  - JSON-tiedosto, joka sisältää tuotetiedot. Tätä tiedostoa luetaan `GetProducts()`-metodissa, jossa tiedot deserialisoidaan `Product`-olioiksi.

- **Views/Home/Product.cshtml**
  - Razor-näkymä, joka renderöi tuotelistan HTML-sivulle `ProductController`-ohjaimen välittämien tietojen perusteella. Näkymä käy tuotteet läpi ja luo jokaisesta tuotekortin.

### Muut tiedostot

- **wwwroot/js/site.js**
  - JavaScript-tiedosto, joka lataa tuotekorttien otsikot isoilla kirjaimilla ja muotoilee hinnat oikeaan valuuttamuotoon.

- **wwwroot/css/site.css**
  - CSS-tyylitiedosto, joka määrittää tuotekorttien ulkoasun. Mukautettu näyttämään tuotteet ruudukossa, jossa on yksinkertainen kehys ja kohdistettu sisältö.

- **Views/Shared/_Layout.cshtml**
  - Layout-tiedosto, jossa on navigointivalikko. Tähän lisättiin "Products"-linkki, jotta käyttäjät voivat helposti siirtyä tuotesivulle.


## Yhteenveto

Sovelluksessa käytetyt ohjaimet, mallit ja näkymät toimivat yhdessä siten, että HomeController hakee tuotetiedot JSON-tiedostosta,
Product-malli tallentaa ja käsittelee tiedot, ja Product-näkymä esittää tiedot käyttäjälle.