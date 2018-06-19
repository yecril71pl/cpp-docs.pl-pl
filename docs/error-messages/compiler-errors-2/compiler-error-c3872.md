---
title: C3872 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3872
dev_langs:
- C++
helpviewer_keywords:
- C3872
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3259e87eb8939129ebc84c0a08acab2c7d7c509
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270165"
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