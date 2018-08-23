---
title: przestarzałe (C/C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs:
- C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d51ee23ab4e4be9cf24b913cb0c4ffa325a9bbf5
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465122"
---
# <a name="deprecated-cc"></a>przestarzałe (C/C++)
**Przestarzałe** pragma pozwala wskazać, że funkcja, typ lub innego identyfikatora może nie będą obsługiwane w przyszłości wydania, lub już nie powinny być używane.  
> [!NOTE]
> Aby uzyskać informacje o C ++ 14 `[[deprecated]]` atrybut i wskazówki dotyczące kiedy należy używać atrybutu vs declspec firmy Microsoft lub pragma, zobacz [atrybuty Standard C++](../cpp/attributes.md) atrybutu.
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>Uwagi  
Gdy kompilator napotka identyfikator określony przez **przestarzałe** pragma, generuje ostrzeżenie kompilatora [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).   
  
Można zastąpić nazw makr. Umieść nazwę makra w cudzysłowy lub — w przeciwnym razie rozwinięciu makra zostanie przeprowadzona.  
  
Ponieważ **przestarzałe** pragma działa na wszystkich zgodnych identyfikatorów i nie uwzględnia podpisów, nie jest najlepszym rozwiązaniem dla wycofano określonych wersji dla funkcji przeciążenia. Wszystkie pasujące nazwy funkcji, która jest umieszczany w zakresie wyzwala ostrzeżenia.

Zalecane jest użycie C ++ 14 `[[deprecated]]` atrybutu, jeśli to możliwe, zamiast **przestarzałe** pragmy. Specyficzne dla firmy Microsoft [__declspec(deprecated)](../cpp/deprecated-cpp.md) modyfikator deklaracji jest także lepszym rozwiązaniem w wielu przypadkach niż **przestarzałe** pragmy. `[[deprecated]]` Atrybutu i `__declspec(deprecated)` modyfikator pozwalają na określenie przestarzałe stanu dla określonej formy przeciążonych funkcji. Diagnostyczne ostrzeżenie pojawia się tylko na odwołania do określonego przeciążonej funkcji atrybut lub modyfikator dotyczy.  
  
## <a name="example"></a>Przykład  
  
```cpp  
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
  
Poniższy przykład pokazuje, jak zastąpić klasę:  
  
```cpp  
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