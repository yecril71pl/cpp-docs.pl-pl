---
title: "Kompilatora (poziom 3) ostrzeżenie C4414 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4414
dev_langs: C++
helpviewer_keywords: C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90644170953976d0fb661f1491b59915d5dd3667
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-3-c4414"></a>Kompilator C4414 ostrzegawcze (poziom 3)
"Funkcja": krótki przeskok do funkcji konwertowanej do umieszczonej blisko  
  
 Krótki przechodzi Generowanie instrukcji compact gałęzi do adresu w ograniczonym zakresie z instrukcji. Instrukcja zawiera krótki offset reprezentującą odległość między skok i adresu docelowego definicji funkcji. Podczas łączenia funkcja może być przeniesiony lub w czasie konsolidacji funkcje optymalizacji, które spowodować funkcji do przeniesienia poza zakresem osiągalny z krótkim przesunięcie. Kompilator należy wygenerować specjalne rekord skok, co wymaga instrukcji skok do NAJBLIŻSZEJ lub do tej PORY. Kompilator dokonać konwersji.  
  
 Na przykład następujący kod generuje C4414:  
  
```  
// C4414.cpp  
// compile with: /W3 /c  
// processor: x86  
int DoParityEven();  
int DoParityOdd();  
unsigned char global;  
int __declspec(naked) DoParityEither()  
{  
   __asm  
   {  
      test global,0  
      jpe SHORT DoParityEven  // C4414  
      jmp SHORT DoParityOdd   // C4414  
   }  
}  
```