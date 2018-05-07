---
title: Kompilatora (poziom 3) ostrzeżenie C4414 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1526b20732d7a1b08ec8d753cb64e33e42dd809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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