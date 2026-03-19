# Laboratoire d’Infrastructure Windows Server

![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-blue)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Domain%20Services-blue)
![Linux](https://img.shields.io/badge/Linux-Debian-red)
![Samba](https://img.shields.io/badge/File%20Sharing-Samba-orange)
![Python](https://img.shields.io/badge/Python-Flask-green)
![Projet](https://img.shields.io/badge/Type-Projet%20Homelab-purple)

---
#
![windows-server](https://github.com/user-attachments/assets/a04e70ac-44dc-4b06-846e-d937e97ae17c)

---
# Présentation du projet

Ce projet est un **laboratoire personnel d’infrastructure informatique** visant à simuler un **environnement d’entreprise** basé sur **Windows Server 2022**.

L’objectif est de pratiquer et comprendre les concepts fondamentaux de **l’administration système et réseau** en mettant en place plusieurs services essentiels utilisés dans les infrastructures professionnelles.

Le laboratoire comprend notamment :

* Déploiement d’un contrôleur de domaine Active Directory
* Configuration d’un serveur DHCP
* Gestion du DNS
* Création et gestion des utilisateurs et groupes
* Application de stratégies de groupe (GPO)
* Intégration d’un système Linux dans le domaine
* Mise en place d’un serveur de fichiers Samba
* Automatisation de l’accès aux ressources
* Installation d’un serveur web IIS

Ce projet vise à reproduire une **architecture hybride Windows / Linux**, très courante dans les infrastructures informatiques modernes.

---

# Architecture de l’infrastructure

Architecture simplifiée du laboratoire :

```
<svg xmlns="http://www.w3.org/2000/svg" style="cursor:pointer;max-width:100%;max-height:650px;" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="900px" viewBox="-0.5 -0.5 900 650" content="&lt;mxfile&gt;&#10;  &lt;diagram id=&quot;srvben-schema&quot; name=&quot;Page-1&quot;&gt;&#10;    &lt;mxGraphModel dx=&quot;984&quot; dy=&quot;471&quot; grid=&quot;1&quot; gridSize=&quot;10&quot; guides=&quot;1&quot; tooltips=&quot;1&quot; connect=&quot;1&quot; arrows=&quot;1&quot; fold=&quot;1&quot; page=&quot;1&quot; pageScale=&quot;1&quot; pageWidth=&quot;1169&quot; pageHeight=&quot;827&quot; math=&quot;0&quot; shadow=&quot;0&quot;&gt;&#10;      &lt;root&gt;&#10;        &lt;mxCell id=&quot;0&quot; /&gt;&#10;        &lt;mxCell id=&quot;1&quot; parent=&quot;0&quot; /&gt;&#10;        &lt;mxCell id=&quot;bg&quot; value=&quot;&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;fillColor=#f8fafc;strokeColor=none;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;40&quot; y=&quot;20&quot; width=&quot;900&quot; height=&quot;650&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;top&quot; value=&quot;&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;fillColor=#eaf3ff;strokeColor=#1f6feb;strokeWidth=2;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;330&quot; y=&quot;50&quot; width=&quot;320&quot; height=&quot;260&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;top-title&quot; value=&quot;&amp;lt;font style=&amp;quot;font-size:19px;&amp;quot;&amp;gt;&amp;lt;b&amp;gt;🗄 Windows Server&amp;lt;/b&amp;gt;&amp;lt;/font&amp;gt;&amp;lt;br&amp;gt;&amp;lt;font style=&amp;quot;font-size:15px;&amp;quot;&amp;gt;&amp;lt;b&amp;gt;SRVBEN-01&amp;lt;/b&amp;gt;&amp;lt;/font&amp;gt;&quot; style=&quot;rounded=0;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#1f6feb;fontColor=#ffffff;strokeColor=#1f6feb;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;330&quot; y=&quot;50&quot; width=&quot;320&quot; height=&quot;70&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;role1&quot; value=&quot;AD&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#dbeafe;strokeColor=#60a5fa;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;350&quot; y=&quot;140&quot; width=&quot;130&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;role2&quot; value=&quot;DNS&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#dbeafe;strokeColor=#60a5fa;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;500&quot; y=&quot;140&quot; width=&quot;130&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;role3&quot; value=&quot;DHCP&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#dbeafe;strokeColor=#60a5fa;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;350&quot; y=&quot;186&quot; width=&quot;130&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;role4&quot; value=&quot;GPO&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#dbeafe;strokeColor=#60a5fa;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;500&quot; y=&quot;186&quot; width=&quot;130&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;role5&quot; value=&quot;IIS&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#dbeafe;strokeColor=#60a5fa;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;425&quot; y=&quot;232&quot; width=&quot;130&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;j0&quot; value=&quot;&quot; style=&quot;ellipse;whiteSpace=wrap;html=1;aspect=fixed;strokeColor=none;fillColor=none;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;489&quot; y=&quot;348&quot; width=&quot;2&quot; height=&quot;2&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;j1&quot; value=&quot;&quot; style=&quot;ellipse;whiteSpace=wrap;html=1;aspect=fixed;strokeColor=none;fillColor=none;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;279&quot; y=&quot;348&quot; width=&quot;2&quot; height=&quot;2&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;j2&quot; value=&quot;&quot; style=&quot;ellipse;whiteSpace=wrap;html=1;aspect=fixed;strokeColor=none;fillColor=none;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;699&quot; y=&quot;348&quot; width=&quot;2&quot; height=&quot;2&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;e1&quot; style=&quot;edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;endArrow=none;strokeWidth=2;strokeColor=#1f2937;&quot; edge=&quot;1&quot; parent=&quot;1&quot; source=&quot;top&quot; target=&quot;j0&quot;&gt;&#10;          &lt;mxGeometry relative=&quot;1&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;e2&quot; style=&quot;edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;endArrow=none;strokeWidth=2;strokeColor=#1f2937;&quot; edge=&quot;1&quot; parent=&quot;1&quot; source=&quot;j1&quot; target=&quot;j2&quot;&gt;&#10;          &lt;mxGeometry relative=&quot;1&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;left&quot; value=&quot;&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;fillColor=#eefbf3;strokeColor=#16a34a;strokeWidth=2;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;150&quot; y=&quot;390&quot; width=&quot;260&quot; height=&quot;210&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;left-title&quot; value=&quot;&amp;lt;font style=&amp;quot;font-size:16px;&amp;quot;&amp;gt;&amp;lt;b&amp;gt;🖥 Client Windows&amp;lt;/b&amp;gt;&amp;lt;/font&amp;gt;&quot; style=&quot;rounded=0;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#16a34a;fontColor=#ffffff;strokeColor=#16a34a;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;150&quot; y=&quot;390&quot; width=&quot;260&quot; height=&quot;52&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;left-body&quot; value=&quot;Joint au domaine&amp;lt;br&amp;gt;&amp;lt;br&amp;gt;&amp;lt;b&amp;gt;Authentification AD&amp;lt;/b&amp;gt;&quot; style=&quot;rounded=0;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=none;strokeColor=none;fontSize=14;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;170&quot; y=&quot;460&quot; width=&quot;220&quot; height=&quot;120&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;right&quot; value=&quot;&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;fillColor=#fff4eb;strokeColor=#ea580c;strokeWidth=2;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;570&quot; y=&quot;390&quot; width=&quot;280&quot; height=&quot;210&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;right-title&quot; value=&quot;&amp;lt;font style=&amp;quot;font-size:16px;&amp;quot;&amp;gt;&amp;lt;b&amp;gt;🐧 Serveur Debian&amp;lt;/b&amp;gt;&amp;lt;/font&amp;gt;&quot; style=&quot;rounded=0;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#ea580c;fontColor=#ffffff;strokeColor=#ea580c;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;570&quot; y=&quot;390&quot; width=&quot;280&quot; height=&quot;52&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;net-label&quot; value=&quot;🌐 Réseau du domaine&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#e5e7eb;strokeColor=#9ca3af;fontSize=12;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;430&quot; y=&quot;318&quot; width=&quot;160&quot; height=&quot;24&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;right-body&quot; value=&quot;Joint au domaine&quot; style=&quot;rounded=0;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=none;strokeColor=none;fontSize=14;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;600&quot; y=&quot;450&quot; width=&quot;220&quot; height=&quot;26&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;samba&quot; value=&quot;Samba&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#ffedd5;strokeColor=#fb923c;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;610&quot; y=&quot;490&quot; width=&quot;200&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;share&quot; value=&quot;Partage fichiers&quot; style=&quot;rounded=1;whiteSpace=wrap;html=1;align=center;verticalAlign=middle;fillColor=#ffedd5;strokeColor=#fb923c;fontStyle=1;&quot; vertex=&quot;1&quot; parent=&quot;1&quot;&gt;&#10;          &lt;mxGeometry x=&quot;610&quot; y=&quot;536&quot; width=&quot;200&quot; height=&quot;34&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;e3&quot; style=&quot;edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;endArrow=none;strokeWidth=2;strokeColor=#1f2937;&quot; edge=&quot;1&quot; parent=&quot;1&quot; source=&quot;j1&quot; target=&quot;left&quot;&gt;&#10;          &lt;mxGeometry relative=&quot;1&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;        &lt;mxCell id=&quot;e4&quot; style=&quot;edgeStyle=orthogonalEdgeStyle;rounded=0;orthogonalLoop=1;jettySize=auto;html=1;endArrow=none;strokeWidth=2;strokeColor=#1f2937;&quot; edge=&quot;1&quot; parent=&quot;1&quot; source=&quot;j2&quot; target=&quot;right&quot;&gt;&#10;          &lt;mxGeometry relative=&quot;1&quot; as=&quot;geometry&quot; /&gt;&#10;        &lt;/mxCell&gt;&#10;      &lt;/root&gt;&#10;    &lt;/mxGraphModel&gt;&#10;  &lt;/diagram&gt;&#10;&lt;/mxfile&gt;&#10;" onclick="(function(svg){var src=window.event.target||window.event.srcElement;while (src!=null&amp;&amp;src.nodeName.toLowerCase()!='a'){src=src.parentNode;}if(src==null){if(svg.wnd!=null&amp;&amp;!svg.wnd.closed){svg.wnd.focus();}else{var r=function(evt){if(evt.data=='ready'&amp;&amp;evt.source==svg.wnd){svg.wnd.postMessage(decodeURIComponent(svg.getAttribute('content')),'*');window.removeEventListener('message',r);}};window.addEventListener('message',r);svg.wnd=window.open('https://viewer.diagrams.net/?client=1&amp;page=0&amp;edit=_blank');}}})(this);"><defs/><g><g><rect x="0" y="0" width="900" height="650" rx="97.5" ry="97.5" fill="#f8fafc" stroke="none" pointer-events="all" style="fill: light-dark(rgb(248, 250, 252), rgb(21, 23, 25));"/></g><g><rect x="290" y="30" width="320" height="260" rx="39" ry="39" fill="#eaf3ff" stroke="#1f6feb" stroke-width="2" pointer-events="all" style="fill: light-dark(rgb(234, 243, 255), rgb(22, 30, 40)); stroke: light-dark(rgb(31, 111, 235), rgb(87, 155, 255));"/></g><g><rect x="290" y="30" width="320" height="70" fill="#1f6feb" stroke="#1f6feb" pointer-events="all" style="fill: light-dark(rgb(31, 111, 235), rgb(87, 155, 255)); stroke: light-dark(rgb(31, 111, 235), rgb(87, 155, 255));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 318px; height: 1px; padding-top: 65px; margin-left: 291px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #ffffff; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#ffffff, #121212); line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><font style="font-size:19px;"><b>🗄 Windows Server</b></font><br /><font style="font-size:15px;"><b>SRVBEN-01</b></font></div></div></div></foreignObject><text x="450" y="69" fill="#ffffff" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle">🗄 Windows Server...</text></switch></g></g><g><rect x="310" y="120" width="130" height="34" rx="5.1" ry="5.1" fill="#dbeafe" stroke="#60a5fa" pointer-events="all" style="fill: light-dark(rgb(219, 234, 254), rgb(26, 39, 56)); stroke: light-dark(rgb(96, 165, 250), rgb(50, 110, 183));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 128px; height: 1px; padding-top: 137px; margin-left: 311px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">AD</div></div></div></foreignObject><text x="375" y="141" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">AD</text></switch></g></g><g><rect x="460" y="120" width="130" height="34" rx="5.1" ry="5.1" fill="#dbeafe" stroke="#60a5fa" pointer-events="all" style="fill: light-dark(rgb(219, 234, 254), rgb(26, 39, 56)); stroke: light-dark(rgb(96, 165, 250), rgb(50, 110, 183));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 128px; height: 1px; padding-top: 137px; margin-left: 461px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">DNS</div></div></div></foreignObject><text x="525" y="141" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">DNS</text></switch></g></g><g><rect x="310" y="166" width="130" height="34" rx="5.1" ry="5.1" fill="#dbeafe" stroke="#60a5fa" pointer-events="all" style="fill: light-dark(rgb(219, 234, 254), rgb(26, 39, 56)); stroke: light-dark(rgb(96, 165, 250), rgb(50, 110, 183));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 128px; height: 1px; padding-top: 183px; margin-left: 311px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">DHCP</div></div></div></foreignObject><text x="375" y="187" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">DHCP</text></switch></g></g><g><rect x="460" y="166" width="130" height="34" rx="5.1" ry="5.1" fill="#dbeafe" stroke="#60a5fa" pointer-events="all" style="fill: light-dark(rgb(219, 234, 254), rgb(26, 39, 56)); stroke: light-dark(rgb(96, 165, 250), rgb(50, 110, 183));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 128px; height: 1px; padding-top: 183px; margin-left: 461px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">GPO</div></div></div></foreignObject><text x="525" y="187" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">GPO</text></switch></g></g><g><rect x="385" y="212" width="130" height="34" rx="5.1" ry="5.1" fill="#dbeafe" stroke="#60a5fa" pointer-events="all" style="fill: light-dark(rgb(219, 234, 254), rgb(26, 39, 56)); stroke: light-dark(rgb(96, 165, 250), rgb(50, 110, 183));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 128px; height: 1px; padding-top: 229px; margin-left: 386px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">IIS</div></div></div></foreignObject><text x="450" y="233" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">IIS</text></switch></g></g><g><ellipse cx="450" cy="329" rx="1" ry="1" fill="none" stroke="none" pointer-events="all"/></g><g><ellipse cx="240" cy="329" rx="1" ry="1" fill="none" stroke="none" pointer-events="all"/></g><g><ellipse cx="660" cy="329" rx="1" ry="1" fill="none" stroke="none" pointer-events="all"/></g><g><path d="M 450 290 L 450 310 L 450 308 L 450 328" fill="none" stroke="#1f2937" stroke-width="2" stroke-miterlimit="10" pointer-events="stroke" style="stroke: light-dark(rgb(31, 41, 55), rgb(196, 204, 216));"/></g><g><path d="M 241 329 L 659 329" fill="none" stroke="#1f2937" stroke-width="2" stroke-miterlimit="10" pointer-events="stroke" style="stroke: light-dark(rgb(31, 41, 55), rgb(196, 204, 216));"/></g><g><rect x="110" y="370" width="260" height="210" rx="31.5" ry="31.5" fill="#eefbf3" stroke="#16a34a" stroke-width="2" pointer-events="all" style="fill: light-dark(rgb(238, 251, 243), rgb(16, 27, 20)); stroke: light-dark(rgb(22, 163, 74), rgb(39, 160, 83));"/></g><g><rect x="110" y="370" width="260" height="52" fill="#16a34a" stroke="#16a34a" pointer-events="all" style="fill: light-dark(rgb(22, 163, 74), rgb(39, 160, 83)); stroke: light-dark(rgb(22, 163, 74), rgb(39, 160, 83));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 258px; height: 1px; padding-top: 396px; margin-left: 111px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #ffffff; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#ffffff, #121212); line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><font style="font-size:16px;"><b>🖥 Client Windows</b></font></div></div></div></foreignObject><text x="240" y="400" fill="#ffffff" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle">🖥 Client Windows</text></switch></g></g><g><rect x="130" y="440" width="220" height="120" fill="none" stroke="none" pointer-events="all"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 218px; height: 1px; padding-top: 500px; margin-left: 131px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 14px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Joint au domaine<br /><br /><b>Authentification AD</b></div></div></div></foreignObject><text x="240" y="504" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="14px" text-anchor="middle">Joint au domaine...</text></switch></g></g><g><rect x="530" y="370" width="280" height="210" rx="31.5" ry="31.5" fill="#fff4eb" stroke="#ea580c" stroke-width="2" pointer-events="all" style="fill: light-dark(rgb(255, 244, 235), rgb(33, 24, 16)); stroke: light-dark(rgb(234, 88, 12), rgb(242, 117, 51));"/></g><g><rect x="530" y="370" width="280" height="52" fill="#ea580c" stroke="#ea580c" pointer-events="all" style="fill: light-dark(rgb(234, 88, 12), rgb(242, 117, 51)); stroke: light-dark(rgb(234, 88, 12), rgb(242, 117, 51));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 278px; height: 1px; padding-top: 396px; margin-left: 531px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #ffffff; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#ffffff, #121212); line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; "><font style="font-size:16px;"><b>🐧 Serveur Debian</b></font></div></div></div></foreignObject><text x="670" y="400" fill="#ffffff" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle">🐧 Serveur Debian</text></switch></g></g><g><rect x="390" y="298" width="160" height="24" rx="3.6" ry="3.6" fill="#e5e7eb" stroke="#9ca3af" pointer-events="all" style="fill: light-dark(rgb(229, 231, 235), rgb(36, 38, 41)); stroke: light-dark(rgb(156, 163, 175), rgb(92, 98, 108));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 158px; height: 1px; padding-top: 310px; margin-left: 391px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">🌐 Réseau du domaine</div></div></div></foreignObject><text x="470" y="314" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">🌐 Réseau du domaine</text></switch></g></g><g><rect x="560" y="430" width="220" height="26" fill="none" stroke="none" pointer-events="all"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 218px; height: 1px; padding-top: 443px; margin-left: 561px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 14px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; white-space: normal; word-wrap: normal; ">Joint au domaine</div></div></div></foreignObject><text x="670" y="447" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="14px" text-anchor="middle">Joint au domaine</text></switch></g></g><g><rect x="570" y="470" width="200" height="34" rx="5.1" ry="5.1" fill="#ffedd5" stroke="#fb923c" pointer-events="all" style="fill: light-dark(rgb(255, 237, 213), rgb(45, 30, 9)); stroke: light-dark(rgb(251, 146, 60), rgb(175, 84, 10));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 198px; height: 1px; padding-top: 487px; margin-left: 571px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">Samba</div></div></div></foreignObject><text x="670" y="491" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">Samba</text></switch></g></g><g><rect x="570" y="516" width="200" height="34" rx="5.1" ry="5.1" fill="#ffedd5" stroke="#fb923c" pointer-events="all" style="fill: light-dark(rgb(255, 237, 213), rgb(45, 30, 9)); stroke: light-dark(rgb(251, 146, 60), rgb(175, 84, 10));"/></g><g><g transform="translate(-0.5 -0.5)"><switch><foreignObject style="overflow: visible; text-align: left;" pointer-events="none" width="100%" height="100%" requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"><div xmlns="http://www.w3.org/1999/xhtml" style="display: flex; align-items: unsafe center; justify-content: unsafe center; width: 198px; height: 1px; padding-top: 533px; margin-left: 571px;"><div style="box-sizing: border-box; font-size: 0; text-align: center; color: #000000; "><div style="display: inline-block; font-size: 12px; font-family: &quot;Helvetica&quot;; color: light-dark(#000000, #ffffff); line-height: 1.2; pointer-events: all; font-weight: bold; white-space: normal; word-wrap: normal; ">Partage fichiers</div></div></div></foreignObject><text x="670" y="537" fill="light-dark(#000000, #ffffff)" font-family="&quot;Helvetica&quot;" font-size="12px" text-anchor="middle" font-weight="bold">Partage fichiers</text></switch></g></g><g><path d="M 240 330 L 240 370" fill="none" stroke="#1f2937" stroke-width="2" stroke-miterlimit="10" pointer-events="stroke" style="stroke: light-dark(rgb(31, 41, 55), rgb(196, 204, 216));"/></g><g><path d="M 660 330 L 660 350 L 670 350 L 670 370" fill="none" stroke="#1f2937" stroke-width="2" stroke-miterlimit="10" pointer-events="stroke" style="stroke: light-dark(rgb(31, 41, 55), rgb(196, 204, 216));"/></g></g><switch><g requiredFeatures="http://www.w3.org/TR/SVG11/feature#Extensibility"/><a transform="translate(0,-5)" xlink:href="https://www.drawio.com/doc/faq/svg-export-text-problems" target="_blank"><text text-anchor="middle" font-size="10px" x="50%" y="100%">Text is not SVG - cannot display</text></a></switch></svg>
```

---

# Fonctionnalités mises en place

## Active Directory

Les éléments suivants ont été configurés avec succès :

* Création du domaine
* Création des unités d’organisation (OU)
* Création des groupes de sécurité
* Gestion des comptes utilisateurs
* Authentification des utilisateurs

Les utilisateurs créés dans Active Directory ont pu se connecter :

* sur un poste **Windows**
* sur une machine **Debian Linux**

L’authentification Linux a été réalisée avec :

* Kerberos
* SSSD
* Realmd

---

## DHCP et configuration réseau

Le serveur DHCP a été installé et configuré avec succès sur Windows Server.

Les éléments configurés :

* création d’une étendue IPv4
* attribution automatique des adresses IP
* configuration DNS pour le domaine

Les postes Windows reçoivent correctement leur configuration réseau.

Cependant, le comportement du **DHCP côté Linux était parfois ambigu pendant les tests**.
J’aimerais approfondir ce point dans un environnement d’infrastructure plus réaliste.

---

## Stratégies de groupe (GPO)

Plusieurs politiques de sécurité ont été mises en place :

* politique de complexité des mots de passe
* verrouillage de compte
* restriction des clés USB
* restriction du panneau de configuration

Le **test de la politique de mot de passe a fonctionné correctement**, ce qui confirme que les GPO sont bien appliquées.

Cependant, j’aimerais avoir l’opportunité de tester ces politiques **dans un environnement réel avec plusieurs postes et plusieurs services**, afin de mieux comprendre leur comportement à grande échelle.

---

## Intégration Linux dans Active Directory

Une machine **Debian** a été intégrée avec succès dans le domaine Active Directory.

Les outils utilisés :

* realmd
* SSSD
* Kerberos

Les utilisateurs du domaine peuvent ouvrir une session sur Linux avec leurs identifiants Active Directory.

Cela démontre l’interopérabilité entre **Windows et Linux dans une infrastructure commune**.

---

## Serveur de fichiers avec Samba

Un serveur Debian a été configuré comme **serveur de fichiers** intégré à Active Directory.

Fonctionnalités mises en place :

* création d’une arborescence de dossiers
* gestion des permissions avec les ACL Linux
* partage des dossiers via Samba
* gestion des accès basée sur les groupes Active Directory

Les postes Windows peuvent accéder aux partages réseau.

Cependant, **le mappage automatique des lecteurs réseau et la gestion des permissions entre Samba et les GPO se sont révélés plus complexes que prévu**.
C’est un point que je souhaiterais approfondir davantage dans un contexte professionnel.

---

## Serveur Web IIS

Le serveur **IIS** a été installé et configuré avec succès sur Windows Server.

L’environnement web est fonctionnel et prêt à accueillir des applications.

---

# Expérience : Déploiement d’une application Flask

J’ai tenté de déployer une application **Python Flask** sur le serveur IIS.

Dépôt du projet :

👉 Lien vers l’application Flask
(à remplacer par ton lien GitHub)

Même si l’installation de IIS a été réussie, **le déploiement de l’application Flask n’a pas abouti comme je le souhaitais**.

C’est un domaine que j’aimerais améliorer car l’intégration entre :

* Windows Server
* IIS
* applications Python
* authentification Active Directory

représente un cas réel très intéressant en entreprise.

---

# Expérience : Contrôle d’accès basé sur Active Directory

J’ai également tenté de mettre en place un **contrôle d’accès à l’application web basé sur les utilisateurs Active Directory**.

L’objectif était de restreindre l’accès à l’application en fonction :

* des comptes utilisateurs AD
* des groupes de sécurité AD

Cette implémentation n’a pas été entièrement réussie, mais c’est un domaine que je serais très motivé à approfondir dans un environnement réel.

---
# Expérience : Intégration d'un agent Wazuh (Sécurité / SIEM)

Dans le cadre de l'amélioration de l'infrastructure et de l'exploration des solutions de **supervision et de sécurité**, j'ai également expérimenté l'intégration d'un **agent Wazuh**.

Wazuh est une plateforme open-source utilisée pour :

* la détection d'intrusion (HIDS)
* la surveillance de l'intégrité des fichiers (FIM)
* l'analyse des journaux système
* la supervision de la sécurité des systèmes

L'objectif de cette expérimentation était de commencer à transformer l'infrastructure en **environnement supervisé**, similaire à ce que l'on retrouve dans les **centres opérationnels de sécurité (SOC)**.

---

# Surveillance de l'intégrité des fichiers (FIM)

L'une des fonctionnalités testées est le module **File Integrity Monitoring (FIM)**.

Ce module permet de :

* surveiller les fichiers critiques du système
* détecter toute modification non autorisée
* générer des alertes en cas de changement suspect

Dans ce laboratoire, l'agent Wazuh a été testé sur un serveur Windows afin d'observer les événements liés aux modifications de fichiers système.

---

# Capture du système surveillé

Ci-dessous une capture du serveur Windows utilisé pour l'expérimentation de l'agent Wazuh.

![Serveur Windows surveillé](screenshots/server_manager_windows.png)

Cette machine constitue le **serveur principal de l'infrastructure** et héberge plusieurs services critiques :

* Active Directory
* DNS
* DHCP
* IIS

L'objectif futur serait de **superviser l'ensemble des machines du laboratoire** afin d'avoir une vision centralisée des événements de sécurité.

---

# Perspectives d'amélioration

Si l'infrastructure évolue, je souhaiterais approfondir les éléments suivants :

* déploiement d'agents Wazuh sur toutes les machines
* centralisation des logs de sécurité
* détection d'activités suspectes
* mise en place d'un mini **SOC (Security Operations Center)** pour le laboratoire
* corrélation des événements de sécurité

Cela permettrait de transformer ce laboratoire en **environnement d'expérimentation complet pour la cybersécurité et la supervision d'infrastructure**.

# Ce que ce projet m’a appris

Ce laboratoire m’a permis de développer des compétences pratiques en :

* administration Windows Server
* gestion d’Active Directory
* intégration Linux dans un domaine
* authentification Kerberos
* gestion des permissions fichiers
* configuration réseau
* dépannage d’infrastructure

Au-delà de la théorie, ce projet m’a confronté à **des problématiques réelles d’administration système**.

---

# Améliorations futures

Si j’avais accès à un laboratoire plus avancé ou à un environnement professionnel, j’aimerais approfondir les aspects suivants :

* déploiement avancé des GPO
* architecture de partage de fichiers en entreprise
* authentification Active Directory pour les applications web
* reverse proxy pour applications Python
* supervision de l’infrastructure (Zabbix / Prometheus)
* SIEM et sécurité (Wazuh) avancé
* sauvegarde automatique des serveurs
* mise en place d’un VPN

---

# Compétences démontrées

Ce projet met en évidence des compétences en :

Administration système
Windows Server
Active Directory
Gestion réseau
Administration Linux
Interopérabilité Windows/Linux
Gestion des permissions
Résolution de problèmes d’infrastructure

---

# Captures

Le dépôt contient plusieurs captures d’écran du laboratoire :

* configuration Active Directory
* configuration DHCP
* stratégies de groupe
* intégration Linux dans le domaine
* serveur Samba
* accès aux partages réseau

---

# Auteur

**Manoach HOSSOU DODO**

Passionné par l’administration système, l’infrastructure informatique et la cybersécurité.

---

# Motivation

Ce projet représente ma démarche personnelle pour **apprendre en construisant une infrastructure complète**.

Certaines parties ont très bien fonctionné, d’autres ont été plus complexes, mais chacune d’entre elles a contribué à renforcer ma compréhension des systèmes.

Je suis particulièrement motivé à **continuer à apprendre et à appliquer ces compétences dans un environnement professionnel réel**.
# windows-server-cybersecurity-lab
Ce projet présente la mise en place d’une infrastructure hybride basée sur Windows Server 2022 et Linux. Il intègre Active Directory, DNS, DHCP, GPO, l’intégration Linux au domaine, un serveur de fichiers Samba avec ACL, le mappage réseau et la supervision avec Wazuh , afin de démontrer des compétences en administration système et cybersécurité.
