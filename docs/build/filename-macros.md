---
title: Makra nazwy pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- filename macros in NMAKE
- NMAKE program, filename macros
ms.assetid: 20afd6b3-5b6c-4e33-9d01-309ce98ef9db
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b2073e4fcb365b3beb10d4040c0f54d9f61a0431
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="filename-macros"></a>Makra nazwy pliku
Makra nazwy pliku są wstępnie zdefiniowane jako nazw plików określonych w zależności (specyfikacje nie pełna nazwa pliku na dysku). Tych makr nie muszą być ujęte w nawiasy, gdy została wywołana; Określ tylko $, jak pokazano.  
  
|Makra|Znaczenie|  
|-----------|-------------|  
|**$@**|Bieżący element docelowy Pełna nazwa (ścieżka, nazwa podstawowa, rozszerzenia), w obecnie określone.|  
|**$$@**|Bieżący element docelowy Pełna nazwa (ścieżka, nazwa podstawowa, rozszerzenia), w obecnie określone. Prawidłowe tylko jako zależne od powstanie zależności.|  
|**$\***|Bieżący element docelowy ścieżka i podstawowa nazwa minus rozszerzenie pliku.|  
|**$\*\***|Wszystkie zależności bieżącą lokalizację docelową.|  
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