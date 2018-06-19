---
title: Makra nazwy pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e28ba5923d8b62973860c0ba503d13682b3c5e79
ms.sourcegitcommit: 3bb7c1c0ceeb8012418e2fff9ae5a7db0fff3877
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458865"
---
# <a name="filename-macros"></a>Makra nazwy pliku
Makra nazwy pliku są wstępnie zdefiniowane jako nazw plików określonych w zależności (specyfikacje nie pełna nazwa pliku na dysku). Tych makr nie muszą być ujęte w nawiasy, gdy została wywołana; Określ tylko $, jak pokazano.  
  
|Macro|Znaczenie|  
|-----------|-------------|  
|**$@**|Bieżący element docelowy Pełna nazwa (ścieżka, nazwa podstawowa, rozszerzenia), w obecnie określone.|  
|**$$@**|Bieżący element docelowy Pełna nazwa (ścieżka, nazwa podstawowa, rozszerzenia), w obecnie określone. Prawidłowe tylko jako zależne od powstanie zależności.|  
|**$&#42;**|Bieżący element docelowy ścieżka i podstawowa nazwa minus rozszerzenie pliku.|  
|**$&#42;&#42;**|Wszystkie zależności bieżącą lokalizację docelową.|  
|**$?**|Wszystkie zależności z sygnaturą czasową nowsze niż bieżący element docelowy.|  
|**$<**|Plik zależny z sygnaturą czasową nowsze niż bieżący element docelowy. Prawidłowe tylko w przypadku poleceń w regułach wnioskowania.|  
  
 Aby określić część filename wstępnie zdefiniowanego makra, Dołącz modyfikator makro i należy umieścić makro zmodyfikowane w nawiasach.  
  
|Modyfikator|Wynikowa część nazwy pliku|  
|--------------|-----------------------------|  
|**D**|Dysk plus katalogu|  
|**B**|Nazwa podstawowa|  
|**F**|Nazwie podstawowej z dodanym rozszerzeniem|  
|**R**|Dysku plus katalog oraz nazwę podstawową|  
  
## <a name="see-also"></a>Zobacz też  
 [Specjalne makra NMAKE](../build/special-nmake-macros.md)
