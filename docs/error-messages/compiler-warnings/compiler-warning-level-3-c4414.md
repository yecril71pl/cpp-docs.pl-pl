---
title: "Kompilatora (poziom 3) ostrzeżenie C4414 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 76745a1cf505a685bcb9a6d2e74faf98bad77556
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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