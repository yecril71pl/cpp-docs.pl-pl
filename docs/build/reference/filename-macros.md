---
title: Makra nazwy pliku
ms.date: 11/04/2016
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
ms.openlocfilehash: 54527c6f06bee396fdc7419647c607f8979c6a38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271245"
---
# <a name="filename-macros"></a>Makra nazwy pliku

Makra nazwy pliku są wstępnie zdefiniowane jako nazwy plików określone w zależności (specyfikacje nie pełna nazwa pliku na dysku). Te makra nie muszą być ujęte w nawiasy, gdy wywoływany; Podaj tylko $, jak pokazano.

|Macro|Znaczenie|
|-----------|-------------|
|**$\@**|Bieżący obiekt docelowy imię i nazwisko (ścieżka, nazwa podstawowa, rozszerzenia), jak aktualnie określone.|
|**$$\@**|Bieżący obiekt docelowy imię i nazwisko (ścieżka, nazwa podstawowa, rozszerzenia), jak aktualnie określone. Prawidłowy tylko jako zależnych od ustawień lokalnych powstanie zależności.|
|**$&#42;**|Bieżący obiekt docelowy nazwa ścieżki i base minus rozszerzenia pliku.|
|**$&#42;&#42;**|Wszystkie zależności bieżącą lokalizację docelową.|
|**$?**|Wszystkie zależności z sygnaturą czasową nowsze niż bieżący element docelowy.|
|**$<**|Plik zależny z sygnaturą czasową nowsze niż bieżący element docelowy. Prawidłowy tylko w przypadku poleceń w zasadach wnioskowania.|

Aby określić część makra, nazwa_pliku wstępnie zdefiniowanych, Dołącz modyfikator — makro, a następnie dołączyć makra zmodyfikowane w nawiasie.

|Modyfikator|Wynikowy część nazwy pliku|
|--------------|-----------------------------|
|**D**|Dysk i katalog|
|**B**|Nazwa podstawowa|
|**F**|Podstawowa nazwa oraz rozszerzenie|
|**R**|Dysk i katalog, a także nazwę podstawową|

## <a name="see-also"></a>Zobacz także

[Specjalne makra NMAKE](special-nmake-macros.md)
