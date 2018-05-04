---
title: Wypełnienie i wyrównanie struktur Członkowskich | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb090fc283da0a8aa86dac524272d308127059ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="padding-and-alignment-of-structure-members"></a>Wypełnienie i wyrównanie struktur członkowskich
**ANSI 3.5.2.1** wypełnienie i wyrównanie członków struktur i czy pole bitowe można wokół granic jednostkę magazynową  
  
 Elementy członkowskie struktur są przechowywane sekwencyjnie, w kolejności, w której były zadeklarowane: pierwszy element członkowski ma najniższy adres pamięci, a ostatni element członkowski – najwyższy.  
  
 Każdy obiekt danych ma wymaganie wyrównania. Wyrównanie wymagań dla wszystkich danych z wyjątkiem struktur, związków i tablice jest rozmiar obiektu lub bieżący rozmiar pakowania (określony za pomocą obu /Zp lub `pack` pragma, ta wartość jest mniejsza). W przypadku struktur, związków i tablice wymaganie wyrównania jest największego zapotrzebowania wyrównanie jego elementów członkowskich. Każdy obiekt został przydzielony przesunięcia, aby  
  
 *Przesunięcie* `%` *wyrównanie wymaganie* `==` 0    
  
 Sąsiadujące pola bitowe są pakowane w takie same 1-, 2- lub 4-bajtowe jednostki alokacji, jeśli typy całkowite mają taki sam rozmiar i jeśli następne pole bitowe pasuje do bieżącej jednostki alokacji bez przekraczania granicy nałożonej przez wspólne wymagania wyrównania pól bitowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)