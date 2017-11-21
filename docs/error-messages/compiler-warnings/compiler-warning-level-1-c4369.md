---
title: "Kompilatora (poziom 1) ostrzeżenie C4369 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4369
dev_langs: C++
helpviewer_keywords: C4369
ms.assetid: ade87e84-36be-4e00-be99-2930af848feb
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6e3150b60de6019968680a5a7350f09868dd5564
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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