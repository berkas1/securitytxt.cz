---
title: "O security.txt"
date: 2023-03-27T20:40:23+02:00
draft: false
---


Soubor security.txt je textový soubor, který mohou správci webů umístit na předem známou adresu (například `https://example.com/.well-known/security.txt`). Tento soubor obsahuje informace jakým způsobem je možné kontaktovat bezpečnostní tým (případně pověřenou osobu) v případě, že na webu někdo najde bezpečnostní problém a chce jej správným způsobem nahlásit.

security.txt je internetový standard definovaný jako [RFC 9116](https://www.rfc-editor.org/rfc/rfc9116). V tomto dokumentu je možné nalézt atuální specifikace a požadavky na soubor.

## Proč soubor vytvořit

Pokud někdo najde bezpečnostní problém na vašem webu a chce jej nahlásit, tak si jednoduše ověří, zda je na webu dostupný soubor security.txt, jehož adresa je obecně známá. Pokud ano, dozví se přesně jak a kde má chybu nahlásit.

Tento jendoduchý prvek pro zvýšení bezpečnosti již publikují firmy jako [Google](https://www.google.com/.well-known/security.txt), [Facebook](https://www.facebook.com/.well-known/security.txt), [gov.uk](https://www.gov.uk/.well-known/security.txt) a další.


## Kde je soubor umístěn

Soubor by měl být umístěn ve složce `.well-known`, která se nachází v kořenovém adresáři webu, webová adresa by tedy měla vypadat takto:

```html
https://example.com/.well-known/security.txt
```

V případě, že není možné použít složku .well-known je tolerováno i umístění souboru přímo v kořenovém adresáři webu:

```html
https://example.com/security.txt
```

## Obsah souboru

Obsah souboru je ve formátu `key: value`. Nejjednodušší forma souboru obsahuje pouze pole *contact* a *expires*. Pole contact může obsahovat e-mailovou adresu nebo odkaz na kontaktní formulář. Pole expires obsahuje datum (ve formátu ISO 8601), po jehož uplynutí má být obsah *security.txt* považován za neplatný.

Platný soubor security.txt může tedy vypadat takto:

```html
Contact: mailto:security@example.com
Expires: 2025-05-01T00:00:00.000Z
```

Dále mohou následovat pole informujicí čtenáře o způsobu, jak správně nahlásit bezpečnostní problém, zda firma nabízí pracovní pozice související s bezpečností nebo preferovaný jazyk pro kontakt. 

Celý soubor může být také digitálně podepsán pomocí PGP.

## Jak soubor vytvořit

Jedná se o běžný textový soubor, je tedy možné jej vytvořit napsáním v textovém editoru, případně využít jednoduchý formulář (který ohlídá správné formátování) na [webu projektu](https://securitytxt.org/).
