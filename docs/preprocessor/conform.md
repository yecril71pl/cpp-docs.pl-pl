---
title: jest zgodna z | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- conform_CPP
- vc-pragma.conform
dev_langs: C++
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f876c1b921a00c251010d22e2cdd000a405a651
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="conform"></a>conform
**Określonego języka C++**  
  
 Określa zachowanie środowiska wykonawczego [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma conform(name [, show ] [, on | off ] [ [, push | pop ] [, identifier ] ] )  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa*  
 Określa nazwę można zmodyfikować opcję kompilatora. Jedyne prawidłowe *nazwa* jest `forScope`.  
  
 **Pokaż** (opcjonalnie)  
 Powoduje, że bieżące ustawienie *nazwa* (true lub false), który będzie wyświetlany za pomocą ostrzeżenie podczas kompilacji. Na przykład `#pragma conform(forScope, show)`.  
  
 **włączony, wyłączony**(opcjonalnie)  
 Ustawienie *nazwa* do **na** umożliwia [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) — opcja kompilatora. Wartość domyślna to **poza**.  
  
 **wypychania** (opcjonalnie)  
 Wypychanie bieżącej wartości *nazwa* na stosie wewnętrznych kompilatora. Jeśli określisz *identyfikator*, można określić **na** lub **poza** wartość *nazwa* do zostać przeniesiony na stosie. Na przykład `#pragma conform(forScope, push, myname, on)`.  
  
 **POP** (opcjonalnie)  
 Ustawia wartość *nazwa* wartości w górnej części stosu wewnętrznego kompilatora, a następnie POP stosu. Jeśli określono identyfikator z **pop**, stos będzie zostać zdjęte ze stosu wstecz, aż znajdzie rekord z *identyfikator*, który będzie również zostać zdjęte ze stosu; bieżąca wartość dla *nazwa* w następnego rekordu na stosie staje się nową wartość *nazwa*. Jeśli określisz pop wraz z *identyfikator* nie jest w rekordzie na stosie, **pop** jest ignorowana.  
  
 *Identyfikator*(opcjonalnie)  
 Może zostać dołączony do **wypychania** lub **pop** polecenia. Jeśli *identyfikator* jest używany, a następnie **na** lub **poza** specyfikator można również.  
  
## <a name="example"></a>Przykład  
  
```  
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