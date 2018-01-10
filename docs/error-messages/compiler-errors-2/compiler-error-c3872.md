---
title: "C3872 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3872
dev_langs: C++
helpviewer_keywords: C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 327a0300e8df9cbc225e130d69bfe359359a0d6e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3872"></a>C3872 błąd kompilatora
"char": ten znak nie jest dozwolony w identyfikatorze  
  
 Kompilator języka C++ następuje C ++ 11 standard na znaki są dozwolone w identyfikatorze. Tylko niektórych zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znaku początkowego identyfikatora. Aby uzyskać więcej informacji oraz listę dozwolonych znaków i zakresy nazwa zawierająca znaki uniwersalne, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).  
  
 Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjne w przypadku kompilowania kodu C + +/ CLI kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR, należy stosować [standardowe ECMA-335: infrastruktury języka wspólnego (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Poniższy przykład generuje C3872:  
  
```  
// C3872.cpp  
int main() {  
   int abc_\u0040;   // C3872, U+0040 is in base char set  
   int abc_\u3001;   // C3872, U+3001 is not in allowed range  
   int \u30A2_abc_\u3042;   // OK, UCNs in allowed range  
}  
```