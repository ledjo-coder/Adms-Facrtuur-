<!DOCTYPE html>
<html lang="sq">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>Krijo faturë</title>
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,600&family=Instrument+Sans:wght@400;500;600&display=swap">
<style>
:root{--bg:#e8edf0;--panel:#f7f9fa;--ink:#14213d;--mute:#5b6b7a;--line:#cfd8de;--acc:#1f6f5c;--accfg:#fff;--field:#fff;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0f1519;--panel:#182026;--ink:#e6edf1;--mute:#93a3af;--line:#2c3a43;--acc:#3fb598;--accfg:#06241c;--field:#0f1519;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0f1519;--panel:#182026;--ink:#e6edf1;--mute:#93a3af;--line:#2c3a43;--acc:#3fb598;--accfg:#06241c;--field:#0f1519;color-scheme:dark}
html{scroll-padding-top:env(safe-area-inset-top,0px)}
,::before,*::after{box-sizing:border-box}
body{margin:0;background:var(--bg);color:var(--ink);font:15px/1.5 "Instrument Sans",system-ui,sans-serif}
.wrap{display:grid;grid-template-columns:minmax(0,420px) minmax(0,1fr);gap:24px;max-width:1180px;margin:0 auto;padding:20px 16px 90px}
@media (max-width:860px){.wrap{grid-template-columns:minmax(0,1fr)}}
h1{font:600 26px/1.2 Fraunces,Georgia,serif;margin:4px 0 16px}
fieldset{border:1px solid var(--line);background:var(--panel);border-radius:10px;margin:0 0 14px;padding:12px 14px 14px;min-width:0}
legend{font-weight:600;padding:0 6px}
label{display:block;font-size:13px;color:var(--mute);margin-top:8px}
input,textarea,select{width:100%;font:inherit;color:var(--ink);background:var(--field);border:1px solid var(--line);border-radius:6px;padding:8px 10px;margin-top:3px}
textarea{resize:vertical;min-height:60px}
:focus-visible{outline:2px solid var(--acc);outline-offset:1px}
.row{display:grid;grid-template-columns:1fr 1fr;gap:10px}
.item{border-top:1px dashed var(--line);padding-top:8px;margin-top:10px}
.item .row3{display:grid;grid-template-columns:.8fr 1.2fr 1fr auto;gap:8px;align-items:end}
button{font:inherit;cursor:pointer;border-radius:6px;border:1px solid var(--line);background:var(--field);color:var(--ink);padding:8px 12px}
button.pri{background:var(--acc);color:var(--accfg);border-color:var(--acc);font-weight:600}
.add{margin-top:10px;width:100%}
.bar{position:fixed;left:0;right:0;bottom:0;display:flex;gap:10px;justify-content:center;padding:10px 16px calc(10px + env(safe-area-inset-bottom,0px));background:var(--panel);border-top:1px solid var(--line)}
.bar button{flex:1;max-width:260px;padding:11px}
/* Fatura (letra) */
.sheet-box{overflow-x:auto}
.sheet{--a:#1f6f5c;background:#fff;color:#14213d;min-width:560px;padding:40px 42px;border-radius:4px;box-shadow:0 1px 3px rgba(0,0,0,.15);font-size:14px}
.sheet h2{font:600 40px/1 Fraunces,Georgia,serif;margin:0;color:var(--a)}
.sheet .top{display:flex;justify-content:space-between;gap:24px;align-items:flex-start}
.sheet .meta{text-align:right;color:#5b6b7a;line-height:1.6}
.sheet .meta b{color:#14213d}
.sheet .parties{display:grid;grid-template-columns:1fr 1fr;gap:24px;margin:30px 0 24px}
.sheet .tag{font-size:12px;color:#5b6b7a;margin-bottom:3px}
.sheet .pre{white-space:pre-line}
.sheet table{width:100%;border-collapse:collapse}
.sheet th{text-align:left;font-weight:600;border-bottom:2px solid #14213d;padding:8px 6px}
.sheet td{padding:9px 6px;border-bottom:1px solid #dde3e7;vertical-align:top}
.sheet .r{text-align:right;white-space:nowrap}
.sheet .tot{margin:16px 0 0 auto;width:min(300px,100%)}
.sheet .tot div{display:flex;justify-content:space-between;padding:4px 6px}
.sheet .tot .g{font-weight:600;font-size:18px;background:var(--a);color:#fff;border-radius:4px;padding:9px 10px;margin-top:6px}
.sheet .notes{margin-top:32px;color:#5b6b7a;border-top:1px solid #dde3e7;padding-top:12px}
.sheet .logo{display:block;max-height:70px;max-width:220px;object-fit:contain;margin-bottom:12px}
.sheet[data-t=m]{border-top:12px solid var(--a)}
.sheet[data-t=m] h2{font:600 30px/1 "Instrument Sans",system-ui,sans-serif;text-transform:uppercase;letter-spacing:.14em}
.sheet[data-t=m] th{background:var(--a);color:#fff;border:0}
.sheet[data-t=n]{padding:48px 52px}
.sheet[data-t=n] h2{font-size:26px;color:#14213d}
.sheet[data-t=n] th{border-bottom:1px solid #14213d;font-weight:500;color:#5b6b7a}
.sheet[data-t=n] td{border-bottom:0}
.sheet[data-t=n] .tot .g{background:none;color:#14213d;border-top:2px solid var(--a);border-radius:0;padding-left:6px;padding-right:6px}
.sheet[data-t=b]{border-left:16px solid var(--a)}
.sheet[data-t=b] h2{font-size:54px;text-transform:uppercase}
.sheet[data-t=b] th{border-bottom:3px solid var(--a)}
.sheet[data-t=b] tbody tr:nth-child(even) td{background:#f1f5f6}
@media print{
 body{background:#fff}.form,.bar,h1.ui{display:none!important}
 .wrap{display:block;padding:0}.sheet-box{overflow:visible}.sheet{box-shadow:none;min-width:0;padding:0}
 .sheet,.sheet *{-webkit-print-color-adjust:exact;print-color-adjust:exact}
}
</style>
</head>
<body>
<div class="wrap">
<div class="form">
<h1 class="ui">Krijo faturë</h1>
<fieldset><legend data-x="16"></legend>
<div class="row"><label><select data-k="tpl"><option value="c" data-x="17"></option><option value="m" data-x="18"></option><option value="n" data-x="19"></option><option value="b" data-x="20"></option></select></label><label><span data-x="21"></span><input type="color" data-k="col" style="height:38px;padding:2px"></label></div>
</fieldset>
<fieldset><legend>Të dhënat tuaja</legend>
<label><span data-x="23"></span><input type="file" id="logo" accept="image/*"></label>
<button type="button" id="rmlogo" data-x="24" hidden style="margin-top:6px"></button>
<label>Emri i biznesit<input data-k="seller.name" autocomplete="organization"></label>
<label>Adresa<textarea data-k="seller.addr"></textarea></label>
<div class="row"><label>Email<input data-k="seller.email" type="email"></label><label>NIPT / nr. fiskal<input data-k="seller.nid"></label></div>
</fieldset>
<fieldset><legend>Klienti</legend>
<label>Emri<input data-k="client.name"></label>
<label>Adresa<textarea data-k="client.addr"></textarea></label>
<label>Email<input data-k="client.email" type="email"></label>
</fieldset>
<fieldset><legend>Fatura</legend>
<div class="row"><label>Numri<input data-k="no"></label><label>Monedha<select data-k="cur"><option>EUR</option><option>ALL</option><option>USD</option><option>GBP</option><option>CHF</option></select></label></div>
<div class="row"><label>Data<input data-k="date" type="date"></label><label>Afati i pagesës<input data-k="due" type="date"></label></div>
<div class="row"><label><span data-x="0"></span><select id="ctry"></select></label><label><span data-x="1"></span><select data-k="mode"><option value="n" data-x="2"></option><option value="rc" data-x="3"></option><option value="ex" data-x="4"></option><option value="ep" data-x="5"></option></select></label></div>
<div class="row"><label>Zbritje (%)<input data-k="disc" type="number" min="0" step="0.1"></label><label><span data-x="6"></span><input data-k="cvat"></label></div>
</fieldset>
<fieldset><legend>Shërbimet ose produktet</legend>
<div id="items"></div>
<button class="add" id="add" type="button">Shto rresht</button>
</fieldset>
<fieldset><legend>Shënime</legend>
<textarea data-k="notes" placeholder="P.sh. IBAN, kushtet e pagesës"></textarea>
</fieldset>
</div>
<div class="sheet-box"><div class="sheet" id="sheet"></div></div>
</div>
<div class="bar"><button type="button" id="reset">Faturë e re</button><button type="button" class="pri" id="print">Ruaj si PDF / Printo</button></div>
<script>
(function(){
var today=new Date(),iso=function(d){return d.toISOString().slice(0,10)};
function fresh(){var d=new Date(today);d.setDate(d.getDate()+14);return{no:'FAT-0001',date:iso(today),due:iso(d),cur:'EUR',tax:20,disc:0,country:'AL',tpl:'c',col:'#1f6f5c',logo:'',mode:'n',cvat:'',notes:'',client:{name:'',addr:'',email:''},seller:{name:'',addr:'',email:'',nid:''},items:[{d:'',q:1,p:0}]}}
var S=fresh();
var SQ='Krijo faturë|Të dhënat tuaja|Emri i biznesit|Adresa|NIPT / nr. fiskal|Klienti|Emri|Fatura|Numri|Monedha|Data|Afati i pagesës|TVSH (%)|Zbritje (%)|Shërbimet ose produktet|Përshkrimi|Sasia|Çmimi|Shto rresht|Hiq|Shënime|P.sh. IBAN, kushtet e pagesës|Faturë e re|Ruaj si PDF / Printo|Nga|Për|Nr.|Nëntotali|Zbritje|TVSH|Total';
var D={sq:SQ,
en:'Create invoice|Your details|Business name|Address|Tax ID|Client|Name|Invoice|Number|Currency|Date|Due date|VAT (%)|Discount (%)|Services or products|Description|Qty|Price|Add line|Remove|Notes|E.g. IBAN, payment terms|New invoice|Save as PDF / Print|From|To|No.|Subtotal|Discount|VAT|Total',
bg:'Създай фактура|Вашите данни|Име на фирмата|Адрес|ЕИК / ДДС номер|Клиент|Име|Фактура|Номер|Валута|Дата|Падеж|ДДС (%)|Отстъпка (%)|Услуги или продукти|Описание|Кол.|Цена|Добави ред|Премахни|Бележки|Напр. IBAN, условия на плащане|Нова фактура|Запази като PDF / Печат|От|До|№|Междинна сума|Отстъпка|ДДС|Общо',
hr:'Izradi račun|Vaši podaci|Naziv tvrtke|Adresa|OIB / porezni broj|Klijent|Naziv|Račun|Broj|Valuta|Datum|Rok plaćanja|PDV (%)|Popust (%)|Usluge ili proizvodi|Opis|Kol.|Cijena|Dodaj stavku|Ukloni|Napomene|Npr. IBAN, uvjeti plaćanja|Novi račun|Spremi kao PDF / Ispiši|Od|Za|Br.|Međuzbroj|Popust|PDV|Ukupno',
cs:'Vytvořit fakturu|Vaše údaje|Název firmy|Adresa|IČ / DIČ|Zákazník|Jméno|Faktura|Číslo|Měna|Datum|Splatnost|DPH (%)|Sleva (%)|Služby nebo produkty|Popis|Množ.|Cena|Přidat řádek|Odebrat|Poznámky|Např. IBAN, platební podmínky|Nová faktura|Uložit jako PDF / Tisk|Od|Pro|č.|Mezisoučet|Sleva|DPH|Celkem',
da:'Opret faktura|Dine oplysninger|Virksomhedsnavn|Adresse|CVR-nr.|Kunde|Navn|Faktura|Nummer|Valuta|Dato|Forfaldsdato|Moms (%)|Rabat (%)|Ydelser eller varer|Beskrivelse|Antal|Pris|Tilføj linje|Fjern|Noter|F.eks. IBAN, betalingsbetingelser|Ny faktura|Gem som PDF / Udskriv|Fra|Til|Nr.|Subtotal|Rabat|Moms|Total',
nl:'Factuur maken|Jouw gegevens|Bedrijfsnaam|Adres|BTW-nummer|Klant|Naam|Factuur|Nummer|Valuta|Datum|Vervaldatum|BTW (%)|Korting (%)|Diensten of producten|Omschrijving|Aantal|Prijs|Regel toevoegen|Verwijderen|Notities|Bijv. IBAN, betalingsvoorwaarden|Nieuwe factuur|Opslaan als PDF / Afdrukken|Van|Aan|Nr.|Subtotaal|Korting|BTW|Totaal',
et:'Loo arve|Sinu andmed|Ettevõtte nimi|Aadress|Registri-/KMKR-number|Klient|Nimi|Arve|Number|Valuuta|Kuupäev|Maksetähtaeg|Käibemaks (%)|Allahindlus (%)|Teenused või tooted|Kirjeldus|Kogus|Hind|Lisa rida|Eemalda|Märkused|Nt IBAN, maksetingimused|Uus arve|Salvesta PDF-ina / Prindi|Saatja|Saaja|Nr|Vahesumma|Allahindlus|Käibemaks|Kokku',
fi:'Luo lasku|Omat tietosi|Yrityksen nimi|Osoite|Y-tunnus / ALV-tunnus|Asiakas|Nimi|Lasku|Numero|Valuutta|Päivämäärä|Eräpäivä|ALV (%)|Alennus (%)|Palvelut tai tuotteet|Kuvaus|Määrä|Hinta|Lisää rivi|Poista|Huomautukset|Esim. IBAN, maksuehdot|Uusi lasku|Tallenna PDF:nä / Tulosta|Lähettäjä|Vastaanottaja|Nro|Välisumma|Alennus|ALV|Yhteensä',
fr:'Créer une facture|Vos informations|Nom de l’entreprise|Adresse|N° de TVA / SIRET|Client|Nom|Facture|Numéro|Devise|Date|Échéance|TVA (%)|Remise (%)|Services ou produits|Description|Qté|Prix|Ajouter une ligne|Retirer|Notes|Ex. IBAN, conditions de paiement|Nouvelle facture|Enregistrer en PDF / Imprimer|De|À|N°|Sous-total|Remise|TVA|Total',
de:'Rechnung erstellen|Ihre Angaben|Firmenname|Adresse|Steuernummer / USt-IdNr.|Kunde|Name|Rechnung|Nummer|Währung|Datum|Fälligkeitsdatum|MwSt. (%)|Rabatt (%)|Leistungen oder Produkte|Beschreibung|Menge|Preis|Zeile hinzufügen|Entfernen|Notizen|z. B. IBAN, Zahlungsbedingungen|Neue Rechnung|Als PDF speichern / Drucken|Von|An|Nr.|Zwischensumme|Rabatt|MwSt.|Gesamt',
el:'Δημιουργία τιμολογίου|Τα στοιχεία σας|Επωνυμία|Διεύθυνση|ΑΦΜ|Πελάτης|Όνομα|Τιμολόγιο|Αριθμός|Νόμισμα|Ημερομηνία|Λήξη πληρωμής|ΦΠΑ (%)|Έκπτωση (%)|Υπηρεσίες ή προϊόντα|Περιγραφή|Ποσ.|Τιμή|Προσθήκη γραμμής|Αφαίρεση|Σημειώσεις|π.χ. IBAN, όροι πληρωμής|Νέο τιμολόγιο|Αποθήκευση ως PDF / Εκτύπωση|Από|Προς|Αρ.|Υποσύνολο|Έκπτωση|ΦΠΑ|Σύνολο',
hu:'Számla készítése|Az Ön adatai|Cégnév|Cím|Adószám|Ügyfél|Név|Számla|Szám|Pénznem|Dátum|Fizetési határidő|ÁFA (%)|Kedvezmény (%)|Szolgáltatások vagy termékek|Leírás|Menny.|Ár|Sor hozzáadása|Eltávolítás|Megjegyzések|Pl. IBAN, fizetési feltételek|Új számla|Mentés PDF-ként / Nyomtatás|Kiállító|Vevő|Sz.|Részösszeg|Kedvezmény|ÁFA|Összesen',
ga:'Cruthaigh sonrasc|Do shonraí|Ainm an ghnó|Seoladh|Uimhir CBL|Custaiméir|Ainm|Sonrasc|Uimhir|Airgeadra|Dáta|Dáta dlite|CBL (%)|Lascaine (%)|Seirbhísí nó táirgí|Cur síos|Cainníocht|Praghas|Cuir líne leis|Bain|Nótaí|M.sh. IBAN, téarmaí íocaíochta|Sonrasc nua|Sábháil mar PDF / Priontáil|Ó|Chuig|Uimh.|Fo-iomlán|Lascaine|CBL|Iomlán',
it:'Crea fattura|I tuoi dati|Ragione sociale|Indirizzo|P. IVA / Codice fiscale|Cliente|Nome|Fattura|Numero|Valuta|Data|Scadenza|IVA (%)|Sconto (%)|Servizi o prodotti|Descrizione|Q.tà|Prezzo|Aggiungi riga|Rimuovi|Note|Es. IBAN, condizioni di pagamento|Nuova fattura|Salva come PDF / Stampa|Da|A|N.|Subtotale|Sconto|IVA|Totale',
lv:'Izveidot rēķinu|Jūsu dati|Uzņēmuma nosaukums|Adrese|Reģ. nr. / PVN nr.|Klients|Nosaukums|Rēķins|Numurs|Valūta|Datums|Apmaksas termiņš|PVN (%)|Atlaide (%)|Pakalpojumi vai preces|Apraksts|Daudz.|Cena|Pievienot rindu|Noņemt|Piezīmes|Piem., IBAN, maksājuma noteikumi|Jauns rēķins|Saglabāt kā PDF / Drukāt|No|Kam|Nr.|Starpsumma|Atlaide|PVN|Kopā',
lt:'Sukurti sąskaitą faktūrą|Jūsų duomenys|Įmonės pavadinimas|Adresas|Įmonės / PVM kodas|Klientas|Pavadinimas|Sąskaita faktūra|Numeris|Valiuta|Data|Apmokėti iki|PVM (%)|Nuolaida (%)|Paslaugos ar prekės|Aprašymas|Kiekis|Kaina|Pridėti eilutę|Pašalinti|Pastabos|Pvz., IBAN, mokėjimo sąlygos|Nauja sąskaita|Išsaugoti kaip PDF / Spausdinti|Pardavėjas|Pirkėjas|Nr.|Tarpinė suma|Nuolaida|PVM|Iš viso',
mt:'Oħloq fattura|Id-dettalji tiegħek|Isem in-negozju|Indirizz|Numru tal-VAT|Klijent|Isem|Fattura|Numru|Munita|Data|Data tal-ħlas|VAT (%)|Sconto (%)|Servizzi jew prodotti|Deskrizzjoni|Kwantità|Prezz|Żid linja|Neħħi|Noti|Eż. IBAN, termini ta’ ħlas|Fattura ġdida|Issejvja bħala PDF / Stampa|Minn|Lil|Nru|Subtotal|Sconto|VAT|Total',
pl:'Utwórz fakturę|Twoje dane|Nazwa firmy|Adres|NIP|Klient|Nazwa|Faktura|Numer|Waluta|Data|Termin płatności|VAT (%)|Rabat (%)|Usługi lub produkty|Opis|Ilość|Cena|Dodaj pozycję|Usuń|Uwagi|Np. IBAN, warunki płatności|Nowa faktura|Zapisz jako PDF / Drukuj|Sprzedawca|Nabywca|Nr|Suma częściowa|Rabat|VAT|Razem',
pt:'Criar fatura|Os seus dados|Nome da empresa|Morada|NIF|Cliente|Nome|Fatura|Número|Moeda|Data|Vencimento|IVA (%)|Desconto (%)|Serviços ou produtos|Descrição|Qtd.|Preço|Adicionar linha|Remover|Notas|Ex. IBAN, condições de pagamento|Nova fatura|Guardar como PDF / Imprimir|De|Para|N.º|Subtotal|Desconto|IVA|Total',
ro:'Creează factură|Datele tale|Denumirea firmei|Adresa|CUI / cod fiscal|Client|Nume|Factură|Număr|Monedă|Data|Scadență|TVA (%)|Reducere (%)|Servicii sau produse|Descriere|Cant.|Preț|Adaugă rând|Elimină|Observații|Ex. IBAN, condiții de plată|Factură nouă|Salvează ca PDF / Tipărește|De la|Către|Nr.|Subtotal|Reducere|TVA|Total',
sk:'Vytvoriť faktúru|Vaše údaje|Názov firmy|Adresa|IČO / IČ DPH|Zákazník|Meno|Faktúra|Číslo|Mena|Dátum|Splatnosť|DPH (%)|Zľava (%)|Služby alebo produkty|Popis|Množ.|Cena|Pridať riadok|Odstrániť|Poznámky|Napr. IBAN, platobné podmienky|Nová faktúra|Uložiť ako PDF / Tlačiť|Od|Pre|č.|Medzisúčet|Zľava|DPH|Spolu',
sl:'Ustvari račun|Vaši podatki|Naziv podjetja|Naslov|Davčna številka|Stranka|Ime|Račun|Številka|Valuta|Datum|Rok plačila|DDV (%)|Popust (%)|Storitve ali izdelki|Opis|Količina|Cena|Dodaj vrstico|Odstrani|Opombe|Npr. IBAN, plačilni pogoji|Nov račun|Shrani kot PDF / Natisni|Od|Za|Št.|Vmesna vsota|Popust|DDV|Skupaj',
es:'Crear factura|Tus datos|Nombre de la empresa|Dirección|NIF / CIF|Cliente|Nombre|Factura|Número|Moneda|Fecha|Vencimiento|IVA (%)|Descuento (%)|Servicios o productos|Descripción|Cant.|Precio|Añadir línea|Quitar|Notas|P. ej. IBAN, condiciones de pago|Nueva factura|Guardar como PDF / Imprimir|De|Para|N.º|Subtotal|Descuento|IVA|Total',
sv:'Skapa faktura|Dina uppgifter|Företagsnamn|Adress|Org.nr / momsnr|Kund|Namn|Faktura|Nummer|Valuta|Datum|Förfallodatum|Moms (%)|Rabatt (%)|Tjänster eller produkter|Beskrivning|Antal|Pris|Lägg till rad|Ta bort|Anteckningar|T.ex. IBAN, betalningsvillkor|Ny faktura|Spara som PDF / Skriv ut|Från|Till|Nr|Delsumma|Rabatt|Moms|Totalt',
no:'Lag faktura|Dine opplysninger|Firmanavn|Adresse|Org.nr / MVA-nr.|Kunde|Navn|Faktura|Nummer|Valuta|Dato|Forfallsdato|MVA (%)|Rabatt (%)|Tjenester eller varer|Beskrivelse|Antall|Pris|Legg til linje|Fjern|Notater|F.eks. IBAN, betalingsvilkår|Ny faktura|Lagre som PDF / Skriv ut|Fra|Til|Nr.|Delsum|Rabatt|MVA|Totalt',
uk:'Створити рахунок|Ваші дані|Назва компанії|Адреса|ЄДРПОУ / ІПН|Клієнт|Ім’я|Рахунок|Номер|Валюта|Дата|Строк оплати|ПДВ (%)|Знижка (%)|Послуги або товари|Опис|К-сть|Ціна|Додати рядок|Видалити|Примітки|Напр. IBAN, умови оплати|Новий рахунок|Зберегти як PDF / Друк|Від|Кому|№|Проміжна сума|Знижка|ПДВ|Разом'};
var N={sq:'Shqip',en:'English',bg:'Български',hr:'Hrvatski',cs:'Čeština',da:'Dansk',nl:'Nederlands',et:'Eesti',fi:'Suomi',fr:'Français',de:'Deutsch',el:'Ελληνικά',hu:'Magyar',ga:'Gaeilge',it:'Italiano',lv:'Latviešu',lt:'Lietuvių',mt:'Malti',pl:'Polski',pt:'Português',ro:'Română',sk:'Slovenčina',sl:'Slovenščina',es:'Español',sv:'Svenska',no:'Norsk',uk:'Українська'};
var L='';try{L=localStorage.getItem('fatura-lang')||''}catch(e){}
if(!D[L]){L=(navigator.language||'en').slice(0,2).toLowerCase();if(!D[L])L='en'}
var SRC=SQ.split('|'),CUR=SRC;
function T(i){return CUR[i]}
var C={AT:'20,13,10',BE:'21,12,6',BG:'20,9',HR:'25,13,5',CY:'19,9,5,3',CZ:'21,12',DK:'25',EE:'24,13,9',FI:'25.5,13.5,10',FR:'20,10,5.5,2.1',DE:'19,7',GR:'24,13,6',HU:'27,18,5',IE:'23,13.5,9,4.8',IT:'22,10,5,4',LV:'21,12,5',LT:'21,12,5',LU:'17,14,8,3',MT:'18,12,7,5',NL:'21,9',PL:'23,8,5',PT:'23,13,6',RO:'21,11',SK:'23,19,5',SI:'22,9.5,5',ES:'21,10,4',SE:'25,12,6',AL:'20,6',XK:'18,8',MK:'18,10,5',RS:'20,10',ME:'21',BA:'17',CH:'8.1,3.8,2.6',GB:'20,5',NO:'25,15,12'};
var EU='AT BE BG HR CY CZ DK EE FI FR DE GR HU IE IT LV LT LU MT NL PL PT RO SK SI ES SE',EF='IT PL RO HU HR AL RS';
var XE=['Country','VAT rule','Normal (VAT charged)','Reverse charge (B2B, EU only)','VAT exempt','Export outside the EU (0%)','Client VAT ID','Reverse charge: VAT to be accounted for by the recipient (Art. 196, Directive 2006/112/EC).','VAT not charged: exempt supply or small-business scheme (state the legal basis in your country).','Zero-rated export outside the EU (Art. 146, Directive 2006/112/EC).','VAT rules for','standard rate','reduced rates','An invoice should show: number, date, supplier and customer name and address, VAT IDs, description, quantity, price, taxable amount and VAT per rate, and the legal note for 0% or exempt supplies.','This country may require e-invoicing or fiscalisation through a national system. This page only makes a draft or PDF.','Rates taken from public tables (mid-2026). Reduced rates depend on the product, so confirm with your tax authority or accountant.','Invoice design','Classic','Modern','Minimal','Bold','Colour','Style','Upload logo','Remove logo'];
var XS=['Shteti','Rregulli i TVSH-së','Normale (me TVSH)','Autollogaritje (B2B, vetëm BE)','I çliruar nga TVSH','Eksport jashtë BE-së (0%)','Nr. TVSH i klientit','Autollogaritje: TVSH llogaritet nga marrësi (Neni 196, Direktiva 2006/112/KE).','TVSH nuk aplikohet: furnizim i përjashtuar ose skemë për biznese të vogla (shkruaj bazën ligjore).','Eksport me normë 0% jashtë BE-së (Neni 146, Direktiva 2006/112/KE).','Rregullat e TVSH-së për','norma standarde','norma të reduktuara','Fatura duhet të tregojë: numër, datë, emrin dhe adresën e shitësit dhe blerësit, nr. TVSH, përshkrimin, sasinë, çmimin, bazën e tatueshme dhe TVSH sipas normës, dhe shënimin ligjor për 0% ose të përjashtuara.','Ky shtet mund të kërkojë faturim elektronik ose fiskalizim përmes sistemit kombëtar. Kjo faqe bën vetëm draft ose PDF.','Normat janë marrë nga tabela publike (mesi i 2026). Normat e reduktuara varen nga produkti, ndaj konfirmoji me administratën tatimore ose kontabilistin.','Dizajni i faturës','Klasik','Modern','Minimal','I guximshëm','Ngjyra','Stili','Ngarko logon','Hiq logon'];
var XI=[0,1,2,3,4,5,6,7,8,9,10,11,12,16,17,18,19,20,21,23,24];
var XL={
bg:'Държава|Режим на ДДС|Нормален (с ДДС)|Обратно начисляване (B2B, ЕС)|Освободено от ДДС|Износ извън ЕС (0%)|ДДС номер на клиента|Обратно начисляване на ДДС (чл. 196, 2006/112/ЕО)|Освободена доставка, ДДС не се начислява|Износ, 0% (чл. 146, 2006/112/ЕО)|Правила за ДДС:|стандартна ставка|намалени ставки|Дизайн на фактурата|Класически|Модерен|Минималистичен|Смел|Цвят|Качи лого|Премахни лого',
hr:'Država|Pravilo PDV-a|Uobičajeno (s PDV-om)|Prijenos porezne obveze (B2B, EU)|Oslobađeno PDV-a|Izvoz izvan EU (0%)|PDV ID klijenta|Prijenos porezne obveze (čl. 196, 2006/112/EZ)|Oslobođena isporuka, PDV nije obračunat|Izvoz, 0% (čl. 146, 2006/112/EZ)|Pravila PDV-a za|standardna stopa|snižene stope|Dizajn računa|Klasični|Moderni|Minimalistički|Naglašeni|Boja|Učitaj logotip|Ukloni logotip',
cs:'Země|Režim DPH|Běžný (s DPH)|Přenesená daňová povinnost (B2B, EU)|Osvobozeno od DPH|Vývoz mimo EU (0 %)|DIČ zákazníka|Přenesení daňové povinnosti (čl. 196, 2006/112/ES)|Osvobozené plnění, DPH neúčtováno|Vývoz, 0 % (čl. 146, 2006/112/ES)|Pravidla DPH:|základní sazba|snížené sazby|Vzhled faktury|Klasický|Moderní|Minimalistický|Výrazný|Barva|Nahrát logo|Odebrat logo',
da:'Land|Momsregel|Normal (med moms)|Omvendt betalingspligt (B2B, EU)|Momsfri|Eksport uden for EU (0 %)|Kundens momsnr.|Omvendt betalingspligt (art. 196, 2006/112/EF)|Momsfri levering, moms opkræves ikke|Eksport, 0 % (art. 146, 2006/112/EF)|Momsregler for|standardsats|nedsatte satser|Fakturadesign|Klassisk|Moderne|Minimalistisk|Fed|Farve|Upload logo|Fjern logo',
nl:'Land|BTW-regeling|Normaal (met BTW)|BTW verlegd (B2B, EU)|Vrijgesteld van BTW|Uitvoer buiten de EU (0%)|BTW-nummer klant|BTW verlegd (art. 196, 2006/112/EG)|Vrijgestelde levering, geen BTW berekend|Uitvoer, 0% (art. 146, 2006/112/EG)|BTW-regels voor|standaardtarief|verlaagde tarieven|Factuurontwerp|Klassiek|Modern|Minimalistisch|Opvallend|Kleur|Logo uploaden|Logo verwijderen',
et:'Riik|Käibemaksureegel|Tavaline (käibemaksuga)|Pöördmaksustamine (B2B, EL)|Käibemaksuvaba|Eksport väljapoole ELi (0%)|Kliendi KMKR-number|Pöördmaksustamine (art. 196, 2006/112/EÜ)|Käibemaksuvaba tehing, käibemaksu ei arvestata|Eksport, 0% (art. 146, 2006/112/EÜ)|Käibemaksureeglid:|üldmaksumäär|vähendatud maksumäärad|Arve kujundus|Klassikaline|Moodne|Minimalistlik|Julge|Värv|Laadi logo üles|Eemalda logo',
fi:'Maa|ALV-käsittely|Normaali (ALV:llä)|Käänteinen verovelvollisuus (B2B, EU)|ALV:stä vapaa|Vienti EU:n ulkopuolelle (0 %)|Asiakkaan ALV-tunnus|Käänteinen verovelvollisuus (art. 196, 2006/112/EY)|ALV:stä vapaa myynti, ALV:tä ei veloiteta|Vienti, 0 % (art. 146, 2006/112/EY)|ALV-säännöt:|yleinen verokanta|alennetut verokannat|Laskun ulkoasu|Klassinen|Moderni|Minimalistinen|Rohkea|Väri|Lataa logo|Poista logo',
fr:'Pays|Régime de TVA|Normal (avec TVA)|Autoliquidation (B2B, UE)|Exonéré de TVA|Exportation hors UE (0 %)|N° de TVA du client|Autoliquidation (art. 196, 2006/112/CE)|Opération exonérée, TVA non appliquée|Exportation, 0 % (art. 146, 2006/112/CE)|Règles de TVA pour|taux normal|taux réduits|Modèle de facture|Classique|Moderne|Minimaliste|Audacieux|Couleur|Importer un logo|Supprimer le logo',
de:'Land|USt-Regelung|Normal (mit USt)|Steuerschuldnerschaft des Leistungsempfängers (B2B, EU)|Umsatzsteuerfrei|Ausfuhr außerhalb der EU (0 %)|USt-IdNr. des Kunden|Steuerschuldnerschaft des Leistungsempfängers (Art. 196, 2006/112/EG)|Umsatzsteuerfreie Leistung, keine USt berechnet|Ausfuhrlieferung, 0 % (Art. 146, 2006/112/EG)|Umsatzsteuerregeln für|Regelsatz|ermäßigte Sätze|Rechnungsdesign|Klassisch|Modern|Minimalistisch|Auffällig|Farbe|Logo hochladen|Logo entfernen',
el:'Χώρα|Καθεστώς ΦΠΑ|Κανονικό (με ΦΠΑ)|Αντίστροφη επιβάρυνση (B2B, ΕΕ)|Απαλλαγή από ΦΠΑ|Εξαγωγή εκτός ΕΕ (0%)|ΑΦΜ πελάτη|Αντίστροφη επιβάρυνση (άρθρο 196, 2006/112/ΕΚ)|Απαλλασσόμενη παράδοση, δεν χρεώνεται ΦΠΑ|Εξαγωγή, 0% (άρθρο 146, 2006/112/ΕΚ)|Κανόνες ΦΠΑ για|κανονικός συντελεστής|μειωμένοι συντελεστές|Σχέδιο τιμολογίου|Κλασικό|Μοντέρνο|Μινιμαλιστικό|Έντονο|Χρώμα|Μεταφόρτωση λογοτύπου|Αφαίρεση λογοτύπου',
hu:'Ország|ÁFA-szabály|Normál (ÁFA-val)|Fordított adózás (B2B, EU)|ÁFA-mentes|Export az EU-n kívülre (0%)|Vevő adószáma|Fordított adózás (196. cikk, 2006/112/EK)|Adómentes teljesítés, ÁFA nem kerül felszámításra|Export, 0% (146. cikk, 2006/112/EK)|ÁFA-szabályok:|általános kulcs|kedvezményes kulcsok|Számla kinézete|Klasszikus|Modern|Minimalista|Merész|Szín|Logó feltöltése|Logó eltávolítása',
ga:'Tír|Riail CBL|Gnáth (le CBL)|Muirear ar ais (B2B, AE)|Díolmhaithe ó CBL|Onnmhairú lasmuigh den AE (0%)|Uimhir CBL an chliaint|Muirear ar ais (Airteagal 196, 2006/112/CE)|Soláthar díolmhaithe, gan CBL a ghearradh|Onnmhairú, 0% (Airteagal 146, 2006/112/CE)|Rialacha CBL do|gnáthráta|rátaí laghdaithe|Dearadh an tsonraisc|Clasaiceach|Nua-aimseartha|Íostach|Dána|Dath|Uaslódáil lógó|Bain lógó',
it:'Paese|Regime IVA|Normale (con IVA)|Inversione contabile (B2B, UE)|Esente IVA|Esportazione extra UE (0%)|Partita IVA del cliente|Inversione contabile (art. 196, 2006/112/CE)|Operazione esente, IVA non applicata|Esportazione, 0% (art. 146, 2006/112/CE)|Regole IVA per|aliquota ordinaria|aliquote ridotte|Stile della fattura|Classico|Moderno|Minimale|Deciso|Colore|Carica logo|Rimuovi logo',
lv:'Valsts|PVN režīms|Parastais (ar PVN)|Apgrieztā nodokļa maksāšana (B2B, ES)|Atbrīvots no PVN|Eksports ārpus ES (0%)|Klienta PVN numurs|Apgrieztā nodokļa maksāšana (196. pants, 2006/112/EK)|Atbrīvots darījums, PVN netiek aprēķināts|Eksports, 0% (146. pants, 2006/112/EK)|PVN noteikumi:|standarta likme|samazinātās likmes|Rēķina dizains|Klasisks|Moderns|Minimālistisks|Izteiksmīgs|Krāsa|Augšupielādēt logotipu|Noņemt logotipu',
lt:'Šalis|PVM režimas|Įprastas (su PVM)|Atvirkštinis apmokestinimas (B2B, ES)|Neapmokestinama PVM|Eksportas už ES ribų (0%)|Kliento PVM kodas|Atvirkštinis apmokestinimas (196 str., 2006/112/EB)|Neapmokestinamas tiekimas, PVM netaikomas|Eksportas, 0% (146 str., 2006/112/EB)|PVM taisyklės:|standartinis tarifas|lengvatiniai tarifai|Sąskaitos dizainas|Klasikinis|Modernus|Minimalistinis|Ryškus|Spalva|Įkelti logotipą|Pašalinti logotipą',
mt:'Pajjiż|Regola tal-VAT|Normali (bil-VAT)|Inverżjoni tal-ħlas (B2B, UE)|Eżenti mill-VAT|Esportazzjoni barra mill-UE (0%)|Numru tal-VAT tal-klijent|Inverżjoni tal-ħlas (Artikolu 196, 2006/112/KE)|Fornitura eżenti, VAT mhux imposta|Esportazzjoni, 0% (Artikolu 146, 2006/112/KE)|Regoli tal-VAT għal|rata standard|rati mnaqqsa|Disinn tal-fattura|Klassiku|Modern|Minimalista|Qalbieni|Kulur|Tella’ logo|Neħħi l-logo',
pl:'Kraj|Rodzaj rozliczenia VAT|Standardowe (z VAT)|Odwrotne obciążenie (B2B, UE)|Zwolnione z VAT|Eksport poza UE (0%)|Numer VAT klienta|Odwrotne obciążenie (art. 196, 2006/112/WE)|Dostawa zwolniona, VAT nie jest naliczany|Eksport, 0% (art. 146, 2006/112/WE)|Zasady VAT dla|stawka podstawowa|stawki obniżone|Wygląd faktury|Klasyczny|Nowoczesny|Minimalistyczny|Wyrazisty|Kolor|Prześlij logo|Usuń logo',
pt:'País|Regime de IVA|Normal (com IVA)|Autoliquidação (B2B, UE)|Isento de IVA|Exportação fora da UE (0%)|N.º de IVA do cliente|Autoliquidação (art. 196.º, 2006/112/CE)|Operação isenta, IVA não liquidado|Exportação, 0% (art. 146.º, 2006/112/CE)|Regras de IVA para|taxa normal|taxas reduzidas|Design da fatura|Clássico|Moderno|Minimalista|Marcante|Cor|Carregar logótipo|Remover logótipo',
ro:'Țara|Regim TVA|Normal (cu TVA)|Taxare inversă (B2B, UE)|Scutit de TVA|Export în afara UE (0%)|Cod TVA client|Taxare inversă (art. 196, 2006/112/CE)|Livrare scutită, TVA neaplicat|Export, 0% (art. 146, 2006/112/CE)|Reguli TVA pentru|cotă standard|cote reduse|Design factură|Clasic|Modern|Minimalist|Îndrăzneț|Culoare|Încarcă logo|Elimină logo',
sk:'Krajina|Režim DPH|Bežný (s DPH)|Prenesenie daňovej povinnosti (B2B, EÚ)|Oslobodené od DPH|Vývoz mimo EÚ (0 %)|IČ DPH zákazníka|Prenesenie daňovej povinnosti (čl. 196, 2006/112/ES)|Oslobodené plnenie, DPH sa neúčtuje|Vývoz, 0 % (čl. 146, 2006/112/ES)|Pravidlá DPH:|základná sadzba|znížené sadzby|Vzhľad faktúry|Klasický|Moderný|Minimalistický|Výrazný|Farba|Nahrať logo|Odstrániť logo',
sl:'Država|Obravnava DDV|Običajno (z DDV)|Obrnjena davčna obveznost (B2B, EU)|Oproščeno DDV|Izvoz izven EU (0 %)|ID za DDV stranke|Obrnjena davčna obveznost (čl. 196, 2006/112/ES)|Oproščena dobava, DDV se ne obračuna|Izvoz, 0 % (čl. 146, 2006/112/ES)|Pravila DDV za|splošna stopnja|znižani stopnji|Videz računa|Klasičen|Moderen|Minimalističen|Izrazit|Barva|Naloži logotip|Odstrani logotip',
es:'País|Régimen de IVA|Normal (con IVA)|Inversión del sujeto pasivo (B2B, UE)|Exento de IVA|Exportación fuera de la UE (0 %)|NIF-IVA del cliente|Inversión del sujeto pasivo (art. 196, 2006/112/CE)|Operación exenta, IVA no repercutido|Exportación, 0 % (art. 146, 2006/112/CE)|Normas de IVA para|tipo general|tipos reducidos|Diseño de la factura|Clásico|Moderno|Minimalista|Llamativo|Color|Subir logotipo|Quitar logotipo',
sv:'Land|Momsregel|Normal (med moms)|Omvänd skattskyldighet (B2B, EU)|Momsfri|Export utanför EU (0 %)|Kundens momsnr|Omvänd skattskyldighet (art. 196, 2006/112/EG)|Momsfri leverans, moms debiteras inte|Export, 0 % (art. 146, 2006/112/EG)|Momsregler för|normalsats|reducerade satser|Fakturadesign|Klassisk|Modern|Minimalistisk|Kraftfull|Färg|Ladda upp logotyp|Ta bort logotyp',
no:'Land|MVA-regel|Normal (med MVA)|Omvendt avgiftsplikt (B2B, EU)|Fritatt for MVA|Eksport utenfor EU (0 %)|Kundens MVA-nr.|Omvendt avgiftsplikt (art. 196, 2006/112/EF)|Fritatt levering, MVA beregnes ikke|Eksport, 0 % (art. 146, 2006/112/EF)|MVA-regler for|standardsats|reduserte satser|Fakturadesign|Klassisk|Moderne|Minimalistisk|Kraftig|Farge|Last opp logo|Fjern logo',
uk:'Країна|Режим ПДВ|Звичайний (з ПДВ)|Зворотне нарахування (B2B, ЄС)|Звільнено від ПДВ|Експорт за межі ЄС (0%)|Номер ПДВ клієнта|Зворотне нарахування ПДВ (ст. 196, 2006/112/ЄС)|Звільнена поставка, ПДВ не нараховується|Експорт, 0% (ст. 146, 2006/112/ЄС)|Правила ПДВ для|стандартна ставка|знижені ставки|Дизайн рахунку|Класичний|Сучасний|Мінімалістичний|Виразний|Колір|Завантажити логотип|Видалити логотип'};
function X(i){if(L!=='sq'&&L!=='en'&&XL[L]){var k=XI.indexOf(i);if(k>=0)return XL[L].split('|')[k]}return(L==='sq'?XS:XE)[i]}
function cn(c){var n=c;try{n=new Intl.DisplayNames([L],{type:'region'}).of(c==='GR'?'GR':c)||c}catch(e){}return n===c&&c==='XK'?'Kosovo':n}
function rl(){var a=C[S.country].split(',').map(Number);a.push(0);return a}
function eff(it){return S.mode!=='n'?0:(it.v==null?rl()[0]:it.v)}
function vopts(it){var v=eff(it);return rl().map(function(r){return'<option value="'+r+'"'+(r===v?' selected':'')+'>'+r+'%</option>'}).join('')}
function syncMode(){var m=document.querySelector('[data-k="mode"]'),o=m.querySelector('option[value="rc"]');o.disabled=EU.indexOf(S.country)<0;if(o.disabled&&S.mode==='rc')S.mode='n';m.value=S.mode}
function fill(){document.querySelectorAll('[data-x]').forEach(function(e){e.textContent=X(+e.dataset.x)});
 var s=document.getElementById('ctry');s.innerHTML='';
 Object.keys(C).map(function(c){return[c,cn(c)]}).sort(function(a,b){return a[1].localeCompare(b[1],L)}).forEach(function(p){var o=document.createElement('option');o.value=p[0];o.textContent=p[1];s.appendChild(o)});
 s.value=S.country;syncMode()}
function info(){var d=document.getElementById('info');if(!d)return;var c=S.country,r=rl().slice(0,-1);
 d.querySelector('summary').textContent=X(10)+' '+cn(c);
 var h='<p>'+X(11)+': <b>'+r[0]+'%</b>'+(r.length>1?'; '+X(12)+': '+r.slice(1).join('%, ')+'%':'')+'</p><p>'+X(13)+'</p><p>'+X(15)+'</p>';
 if(EF.indexOf(c)>=0)h+='<p>'+X(14)+'</p>';
 d.querySelector('div').innerHTML=h}
function setLang(l){
 L=l;CUR=D[l].split('|');document.documentElement.lang=l;document.title=CUR[0];
 try{localStorage.setItem('fatura-lang',l)}catch(e){}
 var w=document.createTreeWalker(document.body,NodeFilter.SHOW_TEXT),n;
 while((n=w.nextNode())){var p=n.parentNode;if(p.tagName==='SCRIPT'||p.closest('#sheet,#items,#info')||p.hasAttribute('data-x'))continue;if(n._o==null)n._o=SRC.indexOf(n.nodeValue.trim());if(n._o>=0)n.nodeValue=CUR[n._o]}
 document.querySelector('[data-k="notes"]').placeholder=CUR[21];
 fill();renderItems();render();
}
try{var raw=localStorage.getItem('fatura-v1');if(raw){var o=JSON.parse(raw);S.seller=o.seller||S.seller;S.country=o.country||S.country;S.tpl=o.tpl||S.tpl;S.col=o.col||S.col;S.logo=o.logo||'';S.cur=o.cur||S.cur;S.tax=o.tax!=null?o.tax:S.tax;S.notes=o.notes||'';S.no=o.no||S.no}}catch(e){}
function save(){try{localStorage.setItem('fatura-v1',JSON.stringify({seller:S.seller,country:S.country,tpl:S.tpl,col:S.col,logo:S.logo,cur:S.cur,tax:S.tax,notes:S.notes,no:S.no}))}catch(e){}}
function esc(s){return String(s==null?'':s).replace(/[&<>"]/g,function(c){return{'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;'}[c]})}
function money(n){try{return new Intl.NumberFormat(L,{style:'currency',currency:S.cur}).format(n)}catch(e){return n.toFixed(2)+' '+S.cur}}
function fd(s){if(!s)return'';var p=s.split('-');return p[2]+'.'+p[1]+'.'+p[0]}
function get(path){var a=path.split('.'),o=S;for(var i=0;i<a.length-1;i++)o=o[a[i]];return[o,a[a.length-1]]}
document.querySelectorAll('[data-k]').forEach(function(el){
 var r=get(el.dataset.k);el.value=r[0][r[1]];
 el.addEventListener('input',function(){var r=get(el.dataset.k);r[0][r[1]]=el.type==='number'?(parseFloat(el.value)||0):el.value;render();save()});
});
function renderItems(){
 var box=document.getElementById('items');box.innerHTML='';
 S.items.forEach(function(it,i){
  var w=document.createElement('div');w.className='item';
  w.innerHTML='<label>'+T(15)+'<input data-f="d" value="'+esc(it.d)+'"></label><div class="row3"><label>'+T(16)+'<input data-f="q" type="number" min="0" step="any" value="'+it.q+'"></label><label>'+T(17)+'<input data-f="p" type="number" min="0" step="any" value="'+it.p+'"></label><label>'+T(29)+'<select data-f="v"'+(S.mode!=='n'?' disabled':'')+'>'+vopts(it)+'</select></label><button type="button" aria-label="'+esc(T(19))+'">'+T(19)+'</button></div>';
  w.querySelectorAll('input,select').forEach(function(inp){inp.addEventListener('input',function(){var f=inp.dataset.f;it[f]=f==='d'?inp.value:(parseFloat(inp.value)||0);render()})});
  w.querySelector('button').addEventListener('click',function(){if(S.items.length>1){S.items.splice(i,1)}else{S.items=[{d:'',q:1,p:0}]}renderItems();render()});
  box.appendChild(w);
 });
}
function render(){
 var sub=0,rows='',G={};
 S.items.forEach(function(it){var t=it.q*it.p,rt=eff(it);sub+=t;G[rt]=(G[rt]||0)+t;rows+='<tr><td>'+esc(it.d)+'</td><td class="r">'+it.q+'</td><td class="r">'+money(it.p)+'</td><td class="r">'+rt+'%</td><td class="r">'+money(t)+'</td></tr>'});
 var disc=sub*S.disc/100,net=sub-disc,tax=0,tx='';Object.keys(G).sort(function(a,b){return a-b}).forEach(function(r){var b=G[r]*(1-S.disc/100),v=b*r/100;tax+=v;tx+='<div><span>'+T(29)+' '+r+'% / '+money(b)+'</span><span>'+money(v)+'</span></div>'});var tot=net+tax;
 var h='<div class="top"><div>'+(S.logo?'<img class="logo" src="'+S.logo+'" alt="">':'')+'<h2>'+T(7)+'</h2><div style="margin-top:10px"><b>'+esc(S.seller.name)+'</b></div></div><div class="meta"><div>'+T(26)+' <b>'+esc(S.no)+'</b></div><div>'+T(10)+': <b>'+fd(S.date)+'</b></div><div>'+T(11)+': <b>'+fd(S.due)+'</b></div></div></div>';
 h+='<div class="parties"><div><div class="tag">'+T(24)+'</div><div class="pre">'+esc(S.seller.addr)+'</div><div>'+esc(S.seller.email)+'</div>'+(S.seller.nid?'<div>'+T(4)+': '+esc(S.seller.nid)+'</div>':'')+'</div><div><div class="tag">'+T(25)+'</div><div><b>'+esc(S.client.name)+'</b></div><div class="pre">'+esc(S.client.addr)+'</div><div>'+esc(S.client.email)+'</div>'+(S.cvat?'<div>'+X(6)+': '+esc(S.cvat)+'</div>':'')+'</div></div>';
 h+='<table><thead><tr><th>'+T(15)+'</th><th class="r">'+T(16)+'</th><th class="r">'+T(17)+'</th><th class="r">'+T(29)+'</th><th class="r">'+T(30)+'</th></tr></thead><tbody>'+rows+'</tbody></table>';
 h+='<div class="tot"><div><span>'+T(27)+'</span><span>'+money(sub)+'</span></div>';
 if(S.disc)h+='<div><span>'+T(28)+' ('+S.disc+'%)</span><span>−'+money(disc)+'</span></div>';
 h+=''+tx+'<div class="g"><span>'+T(30)+'</span><span>'+money(tot)+'</span></div></div>';
 if(S.mode!=='n')h+='<div class="notes">'+X(S.mode==='rc'?7:S.mode==='ex'?8:9)+'</div>';
 if(S.notes)h+='<div class="notes pre">'+esc(S.notes)+'</div>';
 var sh=document.getElementById('sheet');sh.dataset.t=S.tpl;sh.style.setProperty('--a',S.col);sh.innerHTML=h;info();var rb=document.getElementById('rmlogo');if(rb)rb.hidden=!S.logo;
}
document.getElementById('add').addEventListener('click',function(){S.items.push({d:'',q:1,p:0});renderItems();render()});
document.getElementById('print').addEventListener('click',function(){try{window.print()}catch(e){}});
document.getElementById('reset').addEventListener('click',function(){
 var n=fresh(),m=(S.no.match(/^(.*?)(\d+)$/));
 if(m){n.no=m[1]+String(parseInt(m[2],10)+1).padStart(m[2].length,'0')}
 n.seller=S.seller;n.country=S.country;n.tpl=S.tpl;n.col=S.col;n.logo=S.logo;n.cur=S.cur;n.tax=S.tax;n.notes=S.notes;S=n;
 document.querySelectorAll('[data-k]').forEach(function(el){var r=get(el.dataset.k);el.value=r[0][r[1]]});
 renderItems();render();save();window.scrollTo(0,0);
});
var sel=document.createElement('select');sel.setAttribute('aria-label','Language');sel.style.marginBottom='12px';
Object.keys(N).forEach(function(k){var o=document.createElement('option');o.value=k;o.textContent=N[k];sel.appendChild(o)});
sel.value=L;sel.addEventListener('change',function(){setLang(sel.value)});
var fm=document.querySelector('.form');fm.insertBefore(sel,fm.querySelector('fieldset'));
var inf=document.createElement('details');inf.id='info';inf.innerHTML='<summary></summary><div></div>';inf.style.cssText='margin:0 0 14px;font-size:13px;color:var(--mute)';fm.appendChild(inf);
document.getElementById('ctry').addEventListener('change',function(e){S.country=e.target.value;S.items.forEach(function(it){delete it.v});syncMode();renderItems();render();save()});
document.querySelector('[data-k="mode"]').addEventListener('change',renderItems);
document.getElementById('logo').addEventListener('change',function(e){var f=e.target.files&&e.target.files[0];if(!f)return;var r=new FileReader();r.onload=function(){var im=new Image();im.onload=function(){var m=Math.min(1,500/im.width,200/im.height),c=document.createElement('canvas');c.width=Math.max(1,Math.round(im.width*m));c.height=Math.max(1,Math.round(im.height*m));c.getContext('2d').drawImage(im,0,0,c.width,c.height);S.logo=c.toDataURL(/png|svg|gif|webp/.test(f.type)?'image/png':'image/jpeg',.9);render();save()};im.src=r.result};r.readAsDataURL(f);e.target.value=''});
document.getElementById('rmlogo').addEventListener('click',function(){S.logo='';render();save()});
setLang(L);
})();
</script>
</body>
</html>
