---
title: Magazynowanie i wyrównanie struktur | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- alignment of structures
- structure storage
- storing structures
- packing structures
ms.assetid: 60ff292f-2595-4f37-ae00-4c4b4f047196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4a70ab5fbeb4a1672279e7e9b617e3b4de1c1b5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="storage-and-alignment-of-structures"></a>Magazynowanie i wyrównanie struktur
**Microsoft Specific**  
  
 Elementy członkowskie struktur są przechowywane sekwencyjnie, w kolejności, w której były zadeklarowane: pierwszy element członkowski ma najniższy adres pamięci, a ostatni element członkowski – najwyższy.  
  
 Każdy obiekt danych ma *wyrównanie wymaganie*. W przypadku struktur, wymagany jest największy z ich elementów członkowskich. Każdy obiekt został przydzielony *przesunięcie* , aby  
  
 *Przesunięcie* `%` *wyrównanie wymaganie* `==` 0  
  
 Sąsiadujące pola bitowe są pakowane w takie same 1-, 2- lub 4-bajtowe jednostki alokacji, jeśli typy całkowite mają taki sam rozmiar i jeśli następne pole bitowe pasuje do bieżącej jednostki alokacji bez przekraczania granicy nałożonej przez wspólne wymagania wyrównania pól bitowych.  
  
 Aby zaoszczędzić miejsce lub zachować zgodność z istniejącymi strukturami danych, możesz chcieć przechowywać struktury w mniej lub bardziej kompaktowy sposób. [/Zp](../build/reference/zp-struct-member-alignment.md)[*n*] — opcja kompilatora i [#pragma pack](../preprocessor/pack.md) kontroli, jak struktury danych jest "opakowane" w pamięci. Jeśli używasz /Zp [*n*] opcji, gdzie *n* jest 1, 2, 4, 8 lub 16, każdy element członkowski struktury po zapisaniu pierwszy na bajt granice, które są wymaganie wyrównanie pola albo pakowania rozmiaru ( *n*), w zależności od jest mniejsza. Wyrażone jako formuła, granice bajtowe są  
  
```  
min( n, sizeof( item ) )  
```  
  
 gdzie *n* rozmiar pakowania wyrażone z /Zp [*n*] opcji i *elementu* jest element członkowski struktury. Domyślny rozmiar pakowania to /Zp8.  
  
 Aby użyć dyrektywy `pack` do określenia pakowania innego, niż określone w wierszu polecenia dla określonej struktury, przed strukturą podaj dyrektywę `pack`, gdzie rozmiar pakowania wynosi 1, 2, 4, 8 lub 16. Aby przywrócić pakowanie podane w wierszu polecenia, określ dyrektywę `pack` bez argumentów.  
  
 Bit pola domyślne do rozmiaru **długi** dla kompilatora C firmy Microsoft. Elementy członkowskie struktury są wyrównane rozmiar typu lub /Zp [*n*] rozmiar, w zależności od jest mniejsza. Domyślny rozmiar to 4.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracje struktur](../c-language/structure-declarations.md)