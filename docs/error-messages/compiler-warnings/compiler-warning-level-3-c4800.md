---
title: "Ostrzeżenie (poziom 3) kompilatora C4800 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4800
dev_langs:
- C++
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 687b0dab996bfbfe2ce30d65b86196383c02b914
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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