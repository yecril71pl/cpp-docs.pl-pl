---
title: Agregacje i unie | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: aggregates [C++], and unions
ms.assetid: 859fc211-b111-4f12-af98-de78e48f9b92
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 74ee1bbcf1a39171b18c09274543c72e0b844748
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="aggregates-and-unions"></a>Agregacje i unie
Innych typów, takich jak tablice, struktur i Unii mieć bardziej rygorystyczne wymagania dotyczące wyrównywania, zapewniając spójne Unii i agregacji magazynu i danych pobierania. Poniżej przedstawiono definicje dla tablic, struktury i Unii:  
  
 Tablica  
 Zawiera grupę uporządkowanych danych sąsiadujących ze sobą obiektów. Każdy obiekt nosi nazwę elementu. Wszystkie elementy w tablicy ma ten sam typ danych i rozmiar.  
  
 Struktura  
 Zawiera grupę uporządkowanej obiektów danych. W odróżnieniu od elementów tablicy obiektów danych w ramach struktury może mieć różne typy danych i rozmiary. Każdy obiekt danych w strukturze nosi nazwę członka.  
  
 Union  
 Obiekt przechowujący dowolny zbiór nazwanych elementów członkowskich. Nazwany zestaw elementów członkowskich mogą być dowolnego typu. Magazyn przydzielony do Unii jest równa magazynu wymaganego przez największy członkiem tej Unii, a także wszelkie uzupełnienia wymagane w celu wyrównywania.  
  
 W poniższej tabeli przedstawiono silnie sugerowane wyrównanie skalarne elementów członkowskich Unii i struktur.  
  
||||  
|-|-|-|  
|Typ skalarne|C — typ danych|Wyrównanie wymagane|  
|**INT8**|`char`|Byte|  
|**UINT8**|`unsigned char`|Byte|  
|**INT16**|**short**|Word|  
|**UINT16**|**short bez znaku**|Word|  
|**INT32**|**int, długi**|Bitowego|  
|**UINT32**|**unsigned int, long bez znaku**|Bitowego|  
|**INT64**|`__int64`|Quadword|  
|**UINT64 —**|**__int64 bez znaku**|Quadword|  
|**FP32 (pojedynczy dokładności)**|**float**|Bitowego|  
|**FP64 (Podwójna precyzja)**|**double**|Quadword|  
|**WSKAŹNIK**|**\***|Quadword|  
|`__m64`|**__m64 — struktura**|Quadword|  
|`__m128`|**__m128 — struktura**|Octaword|  
  
 Mają zastosowanie następujące reguły wyrównanie agregacji:  
  
-   Wyrównanie tablicy jest taka sama jak wyrównania elementów tablicy.  
  
-   Wyrównanie początku struktury lub Unii jest maksymalną wyrównanie poszczególnych członków. Każdy element członkowski w ramach struktury lub Unii muszą być umieszczone na jego prawidłowego wyrównania, zgodnie z definicją w poprzedniej tabeli, które mogą wymagać niejawna wypełnienia wewnętrznej, w zależności od poprzedni element członkowski.  
  
-   Struktura rozmiar musi być wielokrotnością jego dostosowania, które mogą wymagać uzupełniania po ostatnim elemencie członkowskim. Ponieważ struktur i Unii można grupować w tablicach, każdy element tablicy struktura lub związek musi rozpocząć i końcu prawidłowego wyrównania wcześniej określona.  
  
-   Istnieje możliwość wyrównanie w taki sposób, aby mieć większe wymagania dotyczące wyrównywania tak długo, jak wcześniejsze reguły są obsługiwane.  
  
-   Poszczególne kompilatora mogą dostosować pakowania struktury przyczyn rozmiar. Na przykład [/Zp (wyrównanie członka struktury)](../build/reference/zp-struct-member-alignment.md) umożliwia dostosowanie pakowania struktur.  
  
## <a name="see-also"></a>Zobacz też  
 [Typy i magazyn](../build/types-and-storage.md)