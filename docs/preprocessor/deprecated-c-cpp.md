---
title: "przestarzałe (C/C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs: C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ee6f8c77c1596789fcb731833a1fb432e77d7e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="deprecated-cc"></a>przestarzałe (C/C++)
**Przestarzałe** pragma pozwala wskazać, że funkcja, typu lub inny identyfikator może przestanie być obsługiwany w przyszłości wersji lub nie powinny być używane.  
> [!NOTE]
> Informacje o C ++ 14 `[[deprecated]]` atrybutu, wskazówki i o tym, kiedy można użyć tego atrybutu vs declspec firmy Microsoft lub pragma, zobacz [atrybuty Standard C++](../cpp/attributes2.md) atrybutu.
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy kompilator napotka identyfikator określony przez **przestarzałe** pragma, generuje ostrzeżenie kompilatora [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).   
  
 Można zastąpić makr nazwy. Umieść nazwę makra w cudzysłowy, możesz też w rozwinięciu makra zostanie przeprowadzona.  
  
 Ponieważ **przestarzałe** pragma działa na wszystkie identyfikatory zgodne i nie uwzględnia podpisów, nie jest najlepszą opcją w przypadku wycofano określonych wersji przeciążonej funkcji. Wszystkie zgodne nazwę funkcji, która jest umieszczany w zakresie wyzwala ostrzeżenia.

  Zalecane jest użycie C ++ 14 `[[deprecated]]` atrybut, jeśli to możliwe, zamiast **przestarzałe** pragma. Specyficzne dla firmy Microsoft [__declspec(deprecated)](../cpp/deprecated-cpp.md) modyfikator deklaracji również jest lepszym rozwiązaniem w wielu przypadkach niż **przestarzałe** pragma. `[[deprecated]]` Atrybutu i `__declspec(deprecated)` modyfikator umożliwiają określenie przestarzałe stanu dla określonego formularzy przeciążonej funkcji. Diagnostycznych ostrzeżenie pojawia się tylko z odwołań do określonych przeciążonej funkcji atrybutu lub modyfikator dotyczy.  
  
## <a name="example"></a>Przykład  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 Poniższy przykład pokazuje, jak można zastąpić klasy:  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)