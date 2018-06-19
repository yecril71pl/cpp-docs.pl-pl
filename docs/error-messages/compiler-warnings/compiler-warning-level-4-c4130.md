---
title: Kompilatora (poziom 4) ostrzeżenie C4130 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4130
dev_langs:
- C++
helpviewer_keywords:
- C4130
ms.assetid: 45e4c7b2-6b51-41c7-ba5e-941aa5c7d3dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 226b715689e506cb34ea6e7684f9ddcf041e638b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292178"
---
# <a name="compiler-warning-level-4-c4130"></a>Kompilator C4130 ostrzegawcze (poziom 4)
"operator": operacja logiczna na adresie ciągu stałych  
  
 Przy użyciu operatora z adresem literału ciągu znaków powoduje nieoczekiwany kod.  
  
 Poniższy przykład generuje C4130:  
  
```  
// C4130.cpp  
// compile with: /W4  
int main()  
{  
   char *pc;  
   pc = "Hello";  
   if (pc == "Hello") // C4130  
   {  
   }  
}  
```  
  
 **Jeśli** instrukcji porównuje wartość przechowywana we wskaźniku `pc` na adres ciąg "Hello", który jest przydzielony oddzielnie zawsze występuje ciąg w kodzie. **Jeśli** instrukcji porównuje ciąg wskazywana przez `pc` z ciągiem "Hello".  
  
 Aby porównać ciągów, należy użyć `strcmp` funkcji.