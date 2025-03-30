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


