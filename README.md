# Exercici 1
L’organització OWASP Foundation va actualitzar en 2021 el seu Top 10 de vulnerabilitats més trobades en aplicacions web. 
Escull 3 vulnerabilitats d’aquesta llista i descriu-les. Escriu l’impacte que tenen a la seguretat i quins danys pot arribar a fer un atac en aquesta vulnerabilitat. Enumera diferents mesures i tècniques per poder evitar-les.

## A05:2021 - Configuració de Seguretat Incorrecta 

###  Descripció:
Aquesta vulnerabilitat es produeix quan una aplicació o sistema no està configurat de manera segura. El 90% de les aplicacions han estat provades per detectar algun tipus de configuració incorrecta, amb una taxa d'incidència mitjana del 4,5% i més de 208.000 casos de CWEs relacionades. Aquesta vulnerabilitat ascendeix en la llista a causa de la creixent presència de programari altament configurable.
La manca d'un enduriment (hardening) de seguretat adequat, permisos configurats incorrectament en serveis al núvol, funcions innecessàries habilitades (ports, serveis, pàgines, comptes o privilegis), comptes per defecte sense canviar,  missatges d'error massa informatius, i funcions de seguretat deshabilitades són alguns dels indicadors d'aquesta vulnerabilitat. També es considera configuració incorrecta quan els servidors no envien capçaleres o directives de seguretat o no tenen valors segurs configurats, o si el programari està desactualitzat o és vulnerable.

###  Impacte en la Seguretat:
 Una configuració incorrecta pot permetre als atacants accedir a informació sensible, alterar el funcionament del sistema, o fins i tot prendre el control complet. És una vulnerabilitat molt comú perquè moltes vegades es deu a errors humans o a la manca de coneixement de configuracions segures. Sense un procés de configuració de seguretat coordinat i repetible, els sistemes corren un major risc.

###  Danys Potencials:
- Pèrdua de dades: Accés no autoritzat a dades sensibles com informació personal, financera o mèdica.
- Compromís del sistema: L'atacant pot prendre el control del sistema i utilitzar-lo per a activitats malicioses com ara enviar spam, atacar altres sistemes, o robar informació addicional.
- Denegació de servei: L'atacant pot interrompre el funcionament del sistema, fent-lo inaccessible als usuaris legítims.
- Sancions legals: La pèrdua de dades personals pot comportar sancions per incompliment de la normativa de protecció de dades (com el RGPD).
- 
###  Mesures Preventives:
- Plataforma Mínima: Implementar una plataforma amb el mínim de funcions, components, documentació i exemples innecessaris. Eliminar o no instal·lar característiques i frameworks no utilitzats.
- Revisió i Actualització de Configuracions: Revisar i actualitzar les configuracions apropiades per a totes les notes de seguretat, actualitzacions i pegats com a part del procés d'administració de pegats. Revisar els permisos d'emmagatzematge al núvol (com els permisos de bucket de S3).
- Arquitectura Segmentada: Implementar una arquitectura d'aplicació segmentada per proporcionar una separació efectiva i segura entre components o instàncies, amb segmentació, organització en contenidors o grups de seguretat al núvol (ACLs).
- Directives de Seguretat: Enviar directives de seguretat als clients, com ara capçaleres de seguretat.
- Verificació Automatitzada: Implementar un procés automatitzat per verificar l'efectivitat de les configuracions i ajustos en tots els entorns.
###  Exemple:
La configuració del servidor d'aplicacions permet que es retornin als usuaris missatges d'error detallats, com ara traces de pila. Això pot exposar informació confidencial o falles subjacents, com ara versions de components que se sap que són vulnerables.

 ## A06:2021 - Components Vulnerables i Desactualitzats
 
### Descripció:
Aquesta vulnerabilitat apareix quan una aplicació fa servir components de tercers (biblioteques, frameworks) amb vulnerabilitats conegudes, sense estar actualitzats. És una àrea difícil de gestionar, i va ser segona en l'enquesta del Top 10 de la comunitat. La dificultat resideix en la prova i l'avaluació dels riscos que aquests components introdueixen. És l'única categoria sense enumeracions CWE assignades directament, utilitzant un pes d'impacte per defecte.
Ets vulnerable si no coneixes les versions de tots els components (incloent-hi les dependències), el programari no té suport o no està actualitzat, no analitzes regularment les vulnerabilitats ni et subscrius a avisos de seguretat, els desenvolupadors no testen la compatibilitat de les biblioteques actualitzades, o no assegures la configuració dels components.
### Danys Potencials:

- Compromís de l'aplicació: L'atacant pot obtenir accés a l'aplicació, modificar el seu codi, o robar dades.
- Execució de codi remot: L'atacant pot executar codi maliciós al servidor on s'executa l'aplicació.
- Atacs de denegació de servei: L'atacant pot provocar que l'aplicació deixi de funcionar, interrompent el servei als usuaris legítims.
- Escalada de privilegis: L'atacant pot obtenir privilegis més alts en el sistema, permetent-li accedir a recursos que normalment no estarien a la seva disposició.

 ### Impacte:
 Els components vulnerables són punts d'entrada per a atacs, amb un impacte greu potencial, ja que s'executen amb els mateixos privilegis que l'aplicació.
 
### Mesures Preventives:
- Gestió de Pegats: Un procés de gestió de pegats que elimini dependències innecessàries.
- Inventari Continu: Un inventari continu de les versions dels components utilitzats, incloent-hi les seves dependències, utilitzant eines com OWASP Dependency Check.
- Monitorització: Supervisió de fonts de vulnerabilitats com CVE/NVD, amb eines d'anàlisi de composició de programari.
- Fonts Segures: Obtenir components només de fonts oficials i amb paquets signats.
- Pla Continu: Un pla continu per monitorar, classificar i aplicar actualitzacions o canvis.

 ### Exemple
Components que s'executen amb els mateixos privilegis que l'aplicació, on les falles poden ser accidentals (error de codificació) o intencionals (porta del darrere).

 ## A09:2021 - Falles en el Registre i Monitoreig 

### Descripció:
Aquesta vulnerabilitat tracta de la manca de registre (logging) i monitoratge adequats de les activitats d'una aplicació o sistema. Aquesta categoria va sorgir de l'enquesta de la comunitat i ha pujat lleugerament respecte al Top 10 del 2017.  Sense un registre i monitoratge adequats, les bretxes no poden ser detectades. La intenció és donar suport a la detecció, escalat i resposta davant de bretxes actives. Aquesta categoria s'amplia més enllà de CWE-117 (Neutralització incorrecta de sortida per a registres), CWE-223 (Omissió d'informació rellevant per a la seguretat) i CWE-532 (Inserció d'informació sensible en un arxiu de registre).
La manca de registre i monitoratge pot prendre diverses formes: no registrar esdeveniments auditables (inicis de sessió, errors d'inici de sessió, transaccions d'alt valor); generar registres poc clars, inadequats o inexistents; no monitorar els registres d'aplicacions i API per detectar activitats sospitoses; emmagatzemar els registres localment; implementar llindars d'alerta i processos d'escalat incorrectament; no generar alertes durant les proves de penetració o escanejos de seguretat; no detectar ni alertar sobre atacs actius en temps real; i ser vulnerable a la fuga d'informació fent registres i esdeveniments d'alerta visibles per a usuaris o atacants.

### Impacte en la Seguretat:
Impedeix la detecció temprana d'activitats sospitoses, permetent als atacants operar sense ser detectats durant més temps. Això augmenta el risc de compromís i dificulta la resposta a incidents. També afecta la capacitat d'auditoria, la visibilitat, les alertes d'incidents i l'anàlisi forense.ç

### Danys Potencials:

- Dificultat en la detecció d'atacs: Els atacs poden passar desapercebuts durant setmanes, mesos o fins i tot anys, permetent als atacants accedir i manipular dades sense ser detectats.
- Investigació d'incidents limitada: Sense registres adequats, és impossible determinar com es va produir un atac, quins sistemes es van veure afectats i quina informació es va comprometre, dificultant la resposta i recuperació.
- Compliment normatiu deficient: La falta de registre i monitoratge pot comportar l'incompliment de regulacions i normatives de seguretat (com el GDPR), resultant en sancions legals i danys reputacionals.
- 
### Mesures Preventives Clau:
- Registre Exhaustiu: Assegurar-se que tots els errors d'inici de sessió, de control d'accés i de validació d'entrades de dades del costat del servidor es poden registrar amb suficient context per identificar comptes sospitoses o malicioses, i mantenir-ho durant el temps suficient per a un anàlisi forense posterior.
- Format de Registres: Assegurar-se que els registres es generen en un format fàcil de processar per les eines de gestió de registres.
- Codificació: Assegurar-se que les dades de registre es codifiquen correctament per prevenir injeccions o atacs al sistema de monitoratge o registre.
- Transaccions d'Alt Valor: Assegurar-se que les transaccions d'alt valor tenen una traça d'auditoria amb controls d'integritat per evitar la modificació o l'eliminació.
- Alertes i Monitoratge: Els equips de DevSecOps han d'establir alertes i monitoratge efectius per detectar activitats sospitoses i respondre-les ràpidament.
- Pla de Resposta: Establir o adoptar un pla de resposta i recuperació, com el NIST 800-61r2 o posterior.
- Frameworks i Eines: Utilitzar frameworks de protecció d'aplicacions (com ModSecurity de OWASP) i conjunts de programes de correlació de registres de codi obert (com ELK: Elasticsearch, Logstash, Kibana).
  
### Exemple:
 Una gran aerolínia  va tindre una bretxa de seguretat amb pèrdua de dades personals (passaports, targetes de crèdit) de milions de passatgers durant més de 10 anys, degut a un proveïdor de serveis d'emmagatzematge al núvol.


# Exercici 2
Obre el següent enllaç (sql inseckten) i realitza un mínim de 7 nivells fent servir tècniques d’injecció SQL. 

## Copia cada una de les sentències SQL resultant que has realitzat a cada nivell i comenta que has aconseguit.
- jane'; –  (Comentem el codi que valida, comentant codi.)
- ' ; DROP TABLE users; –(Eliminem la taula users.)
- ' OR 1=1; – () (entrem amb l’usuari sense posar cap contraseña, comentant codi i afegint una condició.)
- ' OR 1=1 ORDER BY user_id LIMIT 1 – (entrem amb l’usuari sense posar cap contraseña com al anterior nivell. Pero tenint en compte la restricció que ens han possat fent limi 1.)
- ' UNION select username, password from users; – (Fem una querie per saber les dades i obtenim tots els users i les seves contraseñas.)
- ' UNION SELECT s.salary AS staff_salary FROM staff s WHERE s.firstname = 'Greta Maria' – (Obtenim el salary de Greta Maria utilitzant una querie)
- ' UNION SELECT name, email, salary, employed_since FROM staff – (Obtenim totes les dades de la taula staff, fent una uqeire.)
- 
## Enumera i raona diferents formes que pot evitar un atac per SQL injection en projectes fets amb Razor Pages i Entity Framework. 
1. Ús de LINQ en comptes de consultes SQL directes : Entity Framework permet treballar amb LINQ per executar consultes de manera segura sense concatenar cadenes SQL manualment.
2.  Paràmetres en les consultes SQL : Si per algun motiu cal executar una consulta SQL directa, cal fer-ho amb paràmetres en comptes de concatenació de cadenes.
3.   Validació i sanejament d’entrada d'usuari: Ús de DataAnnotations per validar les dades abans de processar-les (Els [Required] i les RegEx).
4.   Configuració de permisos a la base de dades: Assegurar que l'usuari de la base de dades només tingui accés a les dades necessàries.

# Exercici 3
L’empresa a la qual treballes desenvoluparà una aplicació web de venda d’obres d’art. Els artistes registren les seves obres amb fotografies, títol, descripció i preu.  Els clients poden comprar les obres i poden escriure ressenyes públiques dels artistes a qui han comprat. Tant clients com artistes han d’estar registrats. L’aplicació guarda nom, cognoms, adreça completa, dni i telèfon. En el cas dels artistes guarda les dades bancaries per fer els pagaments. Hi ha un tipus d’usuari Acount Manager que s’encarrega de verificar als nous artistes. Un cop aprovats poden pública i vendre les seves obres.

Ara es vol aplicar aplicant els principis  de seguretat per tal de garantir el servei i la integritat de les dades. T’han encarregat l'elaboració de part de les polítiques de seguretat. Elabora els següents apartats:

## Definició del control d’accés: enumera els rols  i quin accés a dades tenen cada rol: 
1. Client:
   - Pot veure les obres d'art disponibles amb la seva informació pública (imatge, títol, descripció, preu, artista associat)
   - Pot accedir i modificar les seves dades personals (nom, cognoms, adreça, telèfon, DNI, contrasenya).
   - Pot veure les seves compres anteriors.
   - Pot escriure ressenyes sobre els artistes als quals ha comprat una obra.
 2. Artista:
    - Pot gestionar el seu perfil i dades personals (nom, cognoms, DNI, telèfon, adreça, dades bancàries, contrasenya).
    - Pot afegir, modificar i eliminar les seves obres d'art.
    - Pot veure les comandes dels clients que han comprat les seves obres.
    - Pot veure les ressenyes que han deixat sobre el seu perfil i respondre-les.
3. Account Manager:
   - Pot accedir a la llista d’artistes pendents de verificació.
   - Pot aprovar o rebutjar nous artistes.
   - Pot veure les dades personals dels artistes registrats (excepte contrasenyes).
4. Usuari No Registrat (Visitant):
   - Pot veure les obres d’art disponibles (imatge, títol, descripció, preu, artista associat).
   - Pot veure les ressenyes públiques dels artistes.
## Definició de la política de contrasenyes: normes de creació, d’ús i canvi de contrasenyes. Raona si són necessàries diferents polítiques segons el perfil d’usuari:
Normes de creació:
 - La contrasenya ha de tenir un mínim de 12 caràcters.
 - Ha d’incloure almenys una lletra majúscula, una minúscula, un número i un caràcter especial.
 - No es poden reutilitzar les darreres 5 contrasenyes.
   
Normes d’ús i canvi:
 - Els usuaris han de canviar la contrasenya cada 6 mesos.
 - Després de 5 intents fallits, el compte es bloquejarà temporalment.
 - Els usuaris han de rebre una notificació quan es detecti un inici de sessió des d’un dispositiu nou.
   
Polítiques diferents pels usuaris:
 - Artistes: Han de canviar la contrasenya més seguit que els altres usuaris (aprox 3 mesos) per protegir dades bancàries.
 - Account Managers : Han d’utilitzar autenticació de dos factors i canviar la contrasenya encara més seguit que els artistes(aprox 2 mesos).
   
## Avaluació de la informació: determina quin valor tenen les dades que treballa l'aplicació. Determina com tractar les dades més sensibles. Quines dades encriptaries?
- Baixa sensibilitat: Informació pública de les obres d’art.
- Sensibilitat normal : Dades personals (nom, cognoms, adreça, telèfon, ressenyes).
- Alta sensibilitat: DNI, dades bancàries, contrasenyes i historial de compres. Aquestes són les dades que yo encriptaría.
  
# Exercici 4
En el control d’accessos, existeixen mètodes d’autenticació basats en tokens. Defineix l’autenticació basada en tokens. Quins tipus hi ha? Com funciona mitjançant la web? Cerca llibreries .Net que ens poden ajudar a implementar autenticació amb tokens:

L'autenticació basada en tokens és un mètode en el qual un servidor genera un token després d'una autenticació exitosa d'un usuari. Aquest token és utilitzat per verificar la identitat de l'usuari en futures sol·licituds, evitant la necessitat d'enviar credencials en cada petició.
 ## Tipus de tokens:
1. JWT (JSON Web Token)
   - Format compacte i segur basat en JSON.
   - Encapçalat: l'encapçalat proporciona informació sobre el JWT: quin tipus de token és i quin mètode s'ha utilitzat per a signar-ho digitalment.
   - Càrrega útil: qualsevol dada JSON pot anar aquí. Les càrregues útils de JWT per a l'autenticació inclouen afirmacions sobre la identitat de l'usuari en la càrrega útil. També poden incloure informació sobre els permisos de l'usuari, del servidor o del punt final de la API.
   - Signatura digital: la signatura utilitza criptografia per a signar l'encapçalat i la càrrega útil amb una clau per a assegurar que les dades que contenen siguin legítims.
   - Més utilitzats.
 2. Tokens de maquinari
    - Tokens connectats: Dispositius físics com claus USB o targetes intel·ligents que es connecten directament a l'ordinador i transmeten automàticament la informació d'autenticació.
    - Tokens desconnectats: Dispositius independents, com claus electròniques o dispositius que generen codis temporals (TOTP), que l'usuari ha d'introduir manualment per autenticar-se.
 3. Tokens d'accés i d'identificació:
    - Tokens d'accés: Permeten accedir a recursos específics i tenen una durada limitada. Són utilitzats en protocols com OAuth 2.0 per permetre que aplicacions de tercers actuïn en nom de l’usuari.
    - Tokens d'identificació: Contenen informació sobre la identitat de l’usuari i s’utilitzen per autenticar-lo en diferents serveis. Un exemple és el ID Token en OpenID Connect.
 ## Funcionament en la web:
 1. Inici de sessió:
    L'usuari envia les seves credencials (nom d'usuari i contrasenya) mitjançant una sol·licitud HTTP, normalment per mitjà d'un formulari d'inici de sessió a la web.
 2. Generació del token:
    Un cop verificades les credencials, el servidor genera un token d'autenticació (com un JWT - JSON Web Token) que conté informació sobre l'usuari (com la seva identitat i els seus permisos). Aquest token és signat digitalment per garantir la seva integritat i autenticitat.
 3. Enviament del token:
    El servidor retorna el token a l'usuari com a resposta de la sol·licitud d'inici de sessió.
 4.  Ús del token en sol·licituds posteriors:
     Quan l'usuari realitza una sol·licitud a la web per accedir a recursos protegits, envia el token en l'encapçalament HTTP de la sol·licitud (generalment en l'encapçalament Authorization amb el valor Bearer <token>).
 5. Validació del token:
     El servidor rep el token, el valida i comprova que no hagi caducat ni sigui falsificat. Si el token és vàlid, el servidor permet l’accés a la sol·licitud; si no, retorna un error d’autenticació (per exemple, un 401 Unauthorized).
 6. Expiració i renovació del token:
    Els tokens tenen una durada limitada, després de la qual l'usuari haurà de fer ús d'un refresh token (si està configurat) per obtenir un nou token d'autenticació sense haver d'iniciar sessió novament.
## Llibreries:
1.  Microsoft.AspNetCore.Authentication.JwtBearer: https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.JwtBearer
2.  Microsoft.IdentityModel.Tokens : https://www.nuget.org/packages/microsoft.identitymodel.tokens
3.  MSAL.NET: https://learn.microsoft.com/en-us/entra/msal/dotnet/
