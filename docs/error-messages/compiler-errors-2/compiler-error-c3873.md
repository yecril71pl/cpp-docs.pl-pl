---
title: "C3873 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3873
helpviewer_keywords: C3873
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: adbc98bd40b6dcfa4640c416b5ec38640b0ee822
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3873"></a>C3873 błąd kompilatora
"char": ten znak nie jest dozwolona jako pierwszy znak identyfikatora  
  
 Kompilator języka C++ następuje C ++ 11 standard na znaki są dozwolone w identyfikatorze. Tylko niektórych zakresy znaków i uniwersalne nazwy znaków są dozwolone w identyfikatorze. Dodatkowe ograniczenia dotyczą znaku początkowego identyfikatora. Aby uzyskać więcej informacji oraz listę dozwolonych znaków i zakresy nazwa zawierająca znaki uniwersalne, zobacz [identyfikatory](../../cpp/identifiers-cpp.md).  
  
 Zakres znaków dozwolonych w identyfikatorze jest mniej restrykcyjne w przypadku kompilowania kodu C + +/ CLI kodu. Identyfikatory w kodzie skompilowanym za pomocą/CLR, należy stosować [standardowe ECMA-335: infrastruktury języka wspólnego (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 Poniższy przykład generuje C3873:  
  
```  
// C3873.cpp  
int main() {  
   int \u036F_abc;   // C3873, not in allowed range for initial character  
   int abc_\u036F;   // OK, in allowed range for non-initial character  
}  
```