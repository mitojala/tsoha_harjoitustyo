MTB-jännyyspaikat

Sovelluksen avulla voi etsiä ja lisätä tietokantaan maastopyöräily spotteja, joissa on jotain erityistä tai haastavaa. Kyseessä on siis yksittäisiä kohtia maastossa, esimerkiksi pudotus kalliolta alas tai hyppyri. Mitä tahansa, jonka ajaminen kuumottaa normaalia enemmän. Esimerkiksi pääkaupunkiseudulla näitä kohteita on paljonkin, mutta niitä ei ole koottu yhteen paikkaan, johon kaikilla halukkailla olisi helposti pääsy.

Käyttäjä voi olla peruskäyttäjä tai ylläpitäjä.

Käyttäjät voivat lisätä spotteja ja niiden metatietoja kuten spottien tyypin, vaikeusasteen 1 (helppo) - 5 (vaikea) ja sanallisen kuvauksen. Lisäksi spotteihin voi lisätä kuvia niistä tai niiden suorittamisesta.

Spotit näkyvät kartalla ja niitä voi etsiä alueen mukaan.

Käyttäjät voivat merkitä spotteihin suorituksen jolloin voidaan tilastoida esimerkiksi eniten/vähiten suorituksia keränneitä spotteja. Lisäksi muille käyttäjille voi lähettää haasteen.

Ylläpitäjä voi lisätä/poistaa spotteja.

---

Current state:

Basic functions such as user handling, creating mtb spots (with map interface), listing added spots and showing these on map have been enabled. Users can add images to spots when creating these. Users can also leave comments to spots.

Instructions for usage:

User must register in order to use the application.

Admins can remove spots.

Mouse hover on a google maps marker shows the spot name. Clicking on the marker opens an infowindow. Otherwise the functions are self explanatory at the moment.

---

Heroku:

https://tsoha-mtb-spots.herokuapp.com/

Automatic deploys on.

---

Database / PostgreSQL

Users - table of users:

id : integer
username : text
password : text
admin : boolean

Spots - table of mtb spots:

id : integer
user_id: integer
name : text
type : text
description : text
latitude: decimal
longitude: decimal
sent_at : timestamp
has_image : boolean
visible: boolean

Spot images - images of mtb spots:

id : integer
spot_id : integer references spots,
spot_image : bytea

Spot comments - comments made of spots:

id : integer,
content : text,
spot_id : integer references spots,
user_id : integer references users,
sent_at : timestamp

---

Background images:

index: Photo by Luca Beani on Unsplash

---

TODO:

- checkboxes for add_spot spot_type if spot is more than one type? (adds complexity to handling of the input)
- option to manually input coordinates that will update google maps marker position
- map search for spots (postgis?)
- better feedback in register user if username is taken
- last visit information to spot details
- preserve map zoom level for better user experience?
