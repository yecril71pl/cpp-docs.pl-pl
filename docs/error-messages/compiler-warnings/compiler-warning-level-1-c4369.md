---
title: Kompilatora (poziom 1) ostrzeżenie C4369 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4369
dev_langs:
- C++
helpviewer_keywords:
- C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 63445f0713b43ce7fde418ebd9d65403965c07ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276532"
---
# <a name="compiler-warning-level-1-c4369"></a>Kompilator C4369 ostrzegawcze (poziom 1)
"moduł wyliczający": moduł wyliczający wartość "wartość" nie może być reprezentowany jako "type", wartość to "nowa_wartość"  
  
 Moduł wyliczający został obliczony powinien być większy niż największa wartość dla określonego typu podstawowego.  To spowodowało przepełnienie i kompilator opakować wartość modułu wyliczającego do najniższej możliwe wartości dla typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4369.  
  
```  
// C4369.cpp  
// compile with: /W1  
int main() {  
   enum Color: char { red = 0x7e, green, blue };   // C4369  
   enum Color2: char { red2 = 0x7d, green2, blue2};   // OK  
}  
```