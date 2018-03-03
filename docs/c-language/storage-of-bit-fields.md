---
title: "Magazynowanie pól bitowych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4816a241-1580-4d1c-82ed-13d359733959
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1be04ba4c68b2629a5e765788af95a203ae06b34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="storage-of-bit-fields"></a>Magazynowanie pól bitowych
**ANSI 3.5.2.1** kolejność alokacji pól bitowych w int  
  
 Pola bitowe są przydzielane w liczbą całkowitą z przedziału od najmniej znaczący najbardziej znaczącego bitu. W poniższym kodzie  
  
```  
struct mybitfields  
{  
   unsigned a : 4;  
   unsigned b : 5;  
   unsigned c : 7;  
} test;  
  
int main( void )  
{  
   test.a = 2;  
   test.b = 31;  
   test.c = 0;  
}  
```  
  
 bity może być ułożone w następujący sposób:  
  
```  
00000001 11110010  
cccccccb bbbbaaaa  
```  
  
 Ponieważ procesorów 80 x 86 przechowują bajcie wartości będące liczbami całkowitymi przed bajcie, liczbę całkowitą 0x01F2 powyżej powinny być przechowywane w pamięci fizycznej jako 0xF2 następuje 0x01.  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury, złożenia, wyliczenia i pola bitowe](../c-language/structures-unions-enumerations-and-bit-fields.md)