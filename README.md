# IfEverythingGoesBad
```
Fontos!
Lehet használni a github-ot, de mindenki csak a SAJÁTJÁRÓL tudja lehúzni a dolgokat!
Sajnos kiderül a vizsgán ha mástól húztuk le a cuccot!
Lehet saját jegyzetet használni!
Nincs tűzfal, úgyhogy azzal nem kell szenvedni.
Kérhetik az ANSIBLE és a DOCKER verziószámát!
(Itt azért külön leírom a parancsot: ansible --version)

SZINTE MINDEN A GITHUB ALAPJÁN VAN MEGCSINÁLVA, ÚGYHOGY HA VALAMI NEM
LENNE MEG AKKOR A https://github.com/sutiszornyeteg -RŐL HÚZZÁTOK LE ÉS TÖLTSÉTEK
FEL MAGATOKNAK AMIT KELL! NEM VÁLLALOK FELELŐSSÉGET SEMMILYEN HIBÁÉRT!
FÁJLOKAT OLVASSÁTOK EL, MERT NÉMELYIK HELYEN ÁTÍRÁSRA VAN SZÜKSÉG –pl

MINDIG KELL KÉPERNYŐMENTÉST KÉSZÍTENI ÉS AZT ELMENTENI!

Az általam készített jegyzet nem takarja a vizsga 100%-át!



A „tétel”:
Nagy vonalakban hogy miről is szól:
 Virtualbox
 Ubuntu 16.04 (Bridgelt kártya, DHCP által kell kapjon címet)
 Ansible leszedése, telepítése
 git clone - wordpress playbook
 wordpress konfigurálása
 wordpress weblap készítése
Parancsról parancsra:
(csak felidézésből megy a dolog, mert nincs nálam saját gép hogy újra meg tudjam csinálni a dolgokat)
1. Remélem a virtualboxos részt és egyéb dolgokat nem kell magyarázni, mert az
mindenkinek reflexből jön ☺

2. Tipp: SSH-val könnyebben boldogul az ember, ha az ubuntu esetleg angol
billentyűzettel lenne + mehet a ctrl+c ctrl+v.
SSH menete: virtuálisgépneve@virtuálisgépcíme , majd kérni fogja a virtuális gép
jelszavát. Kész is 
PL: vizsgagep@192.168.2.75
3.
a. Ansible lehúzása SAJÁT githubról:
Pl: https://github.com/fiokod/ansible
Belépünk a megfelelő könyvtárba, majd jöhet a telepítés:
sudo bash ansible… (nem emlékszem a nevére, de a tabulátor mindent megold)
b. Ha nem akarunk gitezni, akkor eme imasorokat beírjuk egyesével:
sudo apt update
sudo apt install software-properties-common –í
sudo apt-add-repository ppa:ansible/ansible
sudo apt update
sudo apt install ansible –y
Ha sikerült végrehajtani ezek közül valamelyiket, akkor utána jöhet a verzió számának
a lekérdezése: ansible --version
4. Wordpress: ugyanúgy, mint az Ansible-nél, de leírom. (Ha valakinek a repojában az
ansible és a wordpress esetleg együtt lenne, akkor az megspórolt egy pár parancsot)
Githubról: git clone https://github.com/fiokod/wordpress
sudo bash wordpress… (#tabulátormegintsegít)
5. Wordpress installálása után belépünk a megfelelő könyvtárba, majd szerkesszük meg
az index.html fájlt olyanra, amilyenre a feladat kéri.
6. Emlékeim szerint nem ártana ha a wordpressbe belépünk. Ezt úgy tudjuk megtenni,
hogy a terminálba nyomunk egy ifconfig parancsot (vagy egyéb parancsot amivel
megtudjuk gépünk IP címét), majd a böngészőbe beírva a címet megkapjuk az
oldalunkat, ahova regisztrálni vagy pedig be kell lépni. Szerintem ezt majd a vizsgán
belül elmondják hogy ki mivel hogyan és merre meddig regisztráljon – máskülönben
ahogy esik úgy puffan.
7. Ezek után ha jól tudom akkor kész is minden. De amúgy hajam színe szőke, ráadásul
nyolcad részben zsidó is vagyok, úgyhogy nem szabad bízni bennem 






B „tétel”:
Nagy vonalakban hogy miről is szól:
 Virtualbox
 Ubuntu 16.04 (Bridgelt kártya, DHCP által kell kapjon címet)
 docker motor telepítése
 dockerfile készítése
 docker image készítése
 docker konténer indítása
 webszerver működtetése
MINDENEK ELŐTT SZERETNÉM MEGEMLÍTENI, HOGY EHHEZ KELLENI FOG A DOCKERES
FIÓKOD IS! Úgyhogy ne felejtsük el a vizsga napján a nevet és a jelszót 

//1. Docker telepítése:
//a. Ha van a github-on külön erre repo, akkor szokás szerint jöhet a
//git clone https://github.com/fiokod/dockermc és utána jöhet a 
//sudo bash docker… (nevét nem tudom fejből, úgyhogy tabulátor)

//b. Ha nem lenne githubodon, akkor jönnek az újabb imasorok:
//FROM ubuntu:16.04
//MAINTAINER dockeresneved
//RUN apt-get –y update \
//&& apt-get –y upgrade \
//&& apt-get –y install mc \
//&& apt-get –y clean
//WORKDIR /root


EZ AZ EGÉSZ DOCKER FELADAT ---------------------------------------------------------------------------------------
2. A saját dockerninx repomra alakítva leírom az ezek után történő varázs sorokat is.

git clone https....../grimeroni/nginxVIZSGA.git
cd nginxVIZSGA

SUDO BASH docker-install.sh

cd nginxVIZSGA

sudo docker image build . -t valami
sudo docker container run –d –p 80:80 (a konténer build számának az első 4 számjegye)






Én ezek után csak egy dolgot szeretnék mondani: szopás ha nem gitről szedünk le
mindent .
A dockerngnix repomban van a Dockerfile, ahol maga az ngnix van.
Annak sorai a következők:
FROM nginx
RUN rm /usr/share/nginx/html/*
COPY web /usr/share/nginx/html
EXPOSE 80 443
CMD [’’nginx’’, ’’-g’’, ’’daemon off;’’]
3. A saját dockerninx repomra alakítva leírom az ezek után történő varázs sorokat is.
rm –rf dockerngnix
git clone dockerngnix.git
cd dockerngnix

SUDO BASH docker-install.sh

sudo docker image build . –t valami
sudo container run –d –p 80:80 (a konténer build számának az első 4 számjegye)
4. Ezek után jöhet a gép IP címe (ifconfig és többi paranccsal kideríthető) és látszik is az oldalad

5. MÉG ANNYIT, HOGY!
A repomban van egy web mappa, abban pedig egy index.html. Na már most, kicsit át kellene
alakítani azt, mivel nem hiszem hogy a <title>JUDITKA </title> rész mindenkinek jót fog
tenni. Meg szerintem benne lesz a vizsgafeladatban hogy mit kell belerakni majd a html
fájlba.
És akkor ennyi lett volna a B tétel.
Természetesen ez sem 100%, ugyanis aranyhal reinkarnációja vagyok, és rossz az
emlékezőképességem. 
```
