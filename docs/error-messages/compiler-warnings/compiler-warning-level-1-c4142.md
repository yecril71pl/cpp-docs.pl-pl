---
title: Kompilatora (poziom 1) ostrzeżenie C4142 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4142
dev_langs:
- C++
helpviewer_keywords:
- C4142
ms.assetid: 1fdfc3dc-60a2-4f00-b133-20e400f9b7a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c87b7689cf11ab28c1a6377ff85e1594fd1b5fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4142"></a>Kompilator C4142 ostrzegawcze (poziom 1)
nieszkodliwa ponowna definicja typu  
  
 Typ zostało ponownie zdefiniowane w taki sposób, który nie ma wpływu na wygenerowany kod.  
  
 Aby rozwiązać ten problem, sprawdzając możliwe są następujące przyczyny:  
  
-   Funkcja członkowska klasy pochodnej ma inny typ zwracany z odpowiedniej funkcji członkowskiej klasy podstawowej.  
  
-   Typ zdefiniowany z `typedef` polecenie zostało ponownie zdefiniowane przy użyciu różnych składni.  
  
 Poniższy przykład generuje C4142:  
  
```  
// C4142.c  
// compile with: /W1  
float X2;  
X2 = 2.0 + 1.0;   // C4142  
  
int main() {  
   float X2;  
   X2 = 2.0 + 1.0;   // OK  
}  
```