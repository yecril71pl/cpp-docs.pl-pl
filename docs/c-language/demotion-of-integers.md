---
title: "Zwężanie liczb całkowitych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: demoting integers
ms.assetid: 51fb3654-60b0-4de7-80eb-bd910086c18a
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e09a81ca21f6e00777322178dcdf1c09ef22dd5b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="demotion-of-integers"></a>Zwężanie liczb całkowitych
**ANSI 3.2.1.2** wynik konwersji typu integer na krótszą całkowita lub wynik konwersji całkowitą bez znaku na liczbę całkowitą ze znakiem o równej długości, jeśli wartość nie może być reprezentowany  
  
 Gdy **długi** liczba całkowita jest rzutowane na **krótki**, lub **krótki** jest rzutowane na `char`, najmniej znaczący bajtów zostaną zachowane.  
  
 Na przykład w tym wierszu  
  
```  
short x = (short)0x12345678L;  
```  
  
 przypisuje wartość 0x5678 `x`, a ten wiersz  
  
```  
char y = (char)0x1234;  
```  
  
 przypisuje wartość 0x34 `y`.  
  
 Wzorce bit podpisem zmienne są konwertowane na typy niepodpisane i na odwrót, pozostaną bez zmian. Na przykład rzutowanie -2 (0xFE) wartość bez znaku daje 254 (również 0xFE).  
  
## <a name="see-also"></a>Zobacz też  
 [Liczby całkowite](../c-language/integers.md)