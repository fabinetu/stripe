# Configurare Setari Notice - Shopify

Scopul acestui document este de a integra magazinul shopify cu API-ul notice.ro Va punem la dispozitie si varianta video [aici](https://www.youtube.com/@notice.romania "video").

## 1.Trimitere SMS preluare comanda in Shopify

Prestabilit, API-ul notice va trimite notificari folosind primul sablon din lista de sabloane. Asadar, pentru a customiza acest sablone, accesati pagina de  si editati primul sablon cu textul dorit:

![Sablon!](/images/ss_1.png "Pagina Sabloane")

Lista de variabile dinamice suportate in sablon sunt disponibile [aici](https://documenter.getpostman.com/view/6644801/2s9YyzbxNU#98067b32-680a-4dda-bd61-dcfacbee8f45 "Variabile").


## 2. Creare aplicatie Shopify

Pentru a putea vedea comenzile confirmate prin notice este necesara creearea unei aplicatii shopify.

1. Din stanga jos se merge in Settings.
2. Se acceseaza Apps and sales channels
3. Se da click in dreapta sus pe Develop Apps
4. Se da click pe "Create App"
5. App name poate fi orice nume si se apasa create
6. Se merge la "Configure  Admin API scopes"
7. Se selecteaza urmatoarele permisiuni la ambele sectiuni de orders: write_orders si read_orders si salveaza selectia.

![Permisiuni!](/images/ss_4.png "Permisiuni")
8. In final se apasa butonul install app.
9. Se apasa butonul "Reveal token once" si se copiaza in notepad sau orice editor de text.
![Token!](/images/ss_5.png "Token")
10. In acelasi editor unde a fost copiat acel token, se adauga numele magazinului, care poate fi copiat din URL-ul in care va aflati. Numele este: https://admin.shopify.com/store/{nume_magazin}/settings/ -> copiati {nume_magazin}

## 3. Conectarea finala in aplicatia Notice

1. Accesati contul notice [aici](https://app.notice.ro "Cont Notice").
2. Mergeti la integrare API si bifati Integrare Comenzi Shopify
3. La domeniul shopify adaugati {nume_magazin}.myshopify.com Ex: neaionica.myshopify.com
4. La token Shopify adaugati tokenul copiat de la pasul 9.
5. La cuvinte cheie modificati cuvintele care vor genera adaugarea tagului de comanda confirmata. Aveti niste cuvinte cheie exemplu generate.
### ATENTIE! Orice notififcare continand un cuvant cheie din lista separata prin virgula va modifica comanda ca fiind confirmata!
6. Copiati Webhook Shopify URL si accesati in admin shopify Settings->Notifications->Webhooks.
7. Creati un webhook nou si selectati: la Event: Order Creation, Format: JSON, URL: url-ul tocmai copiat la punctul 6, Webhook API versions: oricare scrie latest. In final apasati Save.
![Webhook!](/images/ss_6.png "Webhook")

### 4. Testati fluxul.
Creati o comanda si verificati ca ati primit notificarea conform sablonului configurat la capitolul 1. Raspundeti la mesaj cu un cuvant cheie setat in capitolul 3.5
