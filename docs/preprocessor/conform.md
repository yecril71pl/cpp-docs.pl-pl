---
title: jest zgodna z | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs:
- C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c6204349731222df99683ddb20b2b2d827b3fcd
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465033"
---
# <a name="conform"></a>conform
**Określonego język C++**  
  
Określa zachowanie środowiska wykonawczego [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
### <a name="parameters"></a>Parametry  
*Nazwa*  
Określa nazwę opcję kompilatora, który ma zostać zmodyfikowana. Jedyne prawidłowe *nazwa* jest `forScope`.  
  
*Pokaż* (opcjonalnie)  
Powoduje, że bieżące ustawienie *nazwa* (true lub false), który ma być wyświetlany za pomocą komunikatu ostrzegawczego podczas kompilacji. Na przykład `#pragma conform(forScope, show)`.  
  
*włączony, wyłączony*(opcjonalnie)  
Ustawienie *nazwa* do *na* umożliwia [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora. Wartość domyślna to *poza*.  
  
*wypychane* (opcjonalnie)  
Wypychanie bieżącej wartości *nazwa* na wewnętrznym stosie kompilatora. Jeśli określisz *identyfikator*, można określić *na* lub *poza* wartość *nazwa* ma zostać wypchnięty na stos. Na przykład `#pragma conform(forScope, push, myname, on)`.  
  
*POP* (opcjonalnie)  
Ustawia wartość *nazwa* wartość u góry wewnętrznego stosu kompilatora, a następnie POP stosu. Jeśli identyfikator jest określany za pomocą *pop*, stos będzie zostać zdjęte ze stosu wstecz, aż znajdzie rekord z *identyfikator*, który będzie również zostać zdjęte ze stosu; bieżąca wartość dla *nazwa* w Następny rekord na stosie staje się nową wartość dla *nazwa*. Jeśli określisz pop wraz z *identyfikator* nie jest w rekordzie na stosie, *pop* jest ignorowana.  
  
*Identyfikator*(opcjonalnie)  
Można włączyć *wypychania* lub *pop* polecenia. Jeśli *identyfikator* jest używany, a następnie *na* lub *poza* specyfikator może również służyć.  
  
## <a name="example"></a>Przykład  
  
```cpp  
// pragma_directive_conform.cpp  
// compile with: /W1  
// C4811 expected  
#pragma conform(forScope, show)  
#pragma conform(forScope, push, x, on)  
#pragma conform(forScope, push, x1, off)  
#pragma conform(forScope, push, x2, off)  
#pragma conform(forScope, push, x3, off)  
#pragma conform(forScope, show)  
#pragma conform(forScope, pop, x1)  
#pragma conform(forScope, show)  
  
int main() {}  
```  
  
## <a name="see-also"></a>Zobacz też  

[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)