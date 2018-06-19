---
title: Ostrzeżenie (poziom 3) kompilatora C4800 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ed4b14ae2f3af3218909d6cd4609f1f45d3d7cc2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293637"
---
# <a name="compiler-warning-level-3-c4800"></a>Ostrzeżenie (poziom 3) kompilatora C4800  
  
> "*typu*": Wymuszanie wartości logicznej "true" lub "fałsz" (ostrzeżenie wydajności)  
  
To ostrzeżenie jest generowany, gdy wartość, która nie jest `bool` jest przypisany lub przekształcić na typ `bool`. Zazwyczaj ten komunikat jest spowodowany przez przypisanie `int` zmienne do `bool` zmienne gdzie `int` zmiennej zawiera tylko wartości **true** i **false**i może być ponownie zadeklarowany jako typ `bool`. Jeśli nie można zmodyfikować wyrażenie, tak aby użyć typu `bool`, następnie można dodać "`!=0`" na wyrażenie, które zapewnia typ wyrażenia `bool`. Rzutowanie na typ wyrażenia `bool` nie wyłączać ostrzeżenie, co jest zgodne z projektem.  
  
To ostrzeżenie nie jest generowany w programie Visual Studio 2017 r.  
  
## <a name="example"></a>Przykład
  
 Poniższy przykład generuje C4800 i pokazuje, jak rozwiązywanie problemu:  
  
```cpp  
// C4800.cpp  
// compile with: /W3  
int main() {  
   int i = 0;  
  
   // To fix, instead try:  
   // bool i = 0;  
  
   bool j = i;   // C4800  
   j++;  
}  
```