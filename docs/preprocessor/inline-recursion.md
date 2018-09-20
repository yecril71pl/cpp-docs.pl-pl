---
title: inline_recursion | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inline_recursion_CPP
- vc-pragma.inline_recursion
dev_langs:
- C++
helpviewer_keywords:
- pragmas, inline_recursion
- inline_recursion pragma
ms.assetid: cfef5791-63b7-45ac-9574-623747b9b9c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2c22a9fa20e663a87d10dcb1e9ba154c921a5bf8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46391310"
---
# <a name="inlinerecursion"></a>inline_recursion
Kontroluje wbudowane rozwijanie bezpośrednich lub wzajemnie rekursywne wywołania funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>Uwagi  
 
Użyj tej pragmie do funkcji kontroli oznaczone jako [wbudowane](../cpp/inline-functions-cpp.md) i [__inline](../cpp/inline-functions-cpp.md) lub funkcje, które kompilator automatycznie rozszerza się w obszarze `/Ob2` opcji. Korzystanie z tej pragmie wymaga [/Ob](../build/reference/ob-inline-function-expansion.md) ustawienia opcji kompilatora, 1 lub 2. Domyślny stan dla **inline_recursion** jest wyłączona. Ta dyrektywa pragma staje się skuteczny przy pierwszym wywołaniu funkcji po pragmy jest widoczne, a nie ma wpływu na definicji funkcji.  
  
**Inline_recursion** pragma Określa, jak zostaną rozwinięte funkcji rekursywnych. Jeśli **inline_recursion** jest wyłączona, a jeśli funkcja śródwierszowa wywołuje sam siebie (bezpośrednio lub pośrednio), funkcja jest rozwinięty tylko jeden raz. Jeśli **inline_recursion** jest włączona, funkcja jest rozwinięty wielokrotnie, dopóki nie osiągnie wartość ustawioną przy użyciu [inline_depth](../preprocessor/inline-depth.md) pragma, wartością domyślną dla funkcji cyklicznych, który jest definiowany przez `inline_depth` pragma lub pojemność ograniczyć.  
  
## <a name="see-also"></a>Zobacz też  
 
[Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[inline_depth](../preprocessor/inline-depth.md)<br/>
[/Ob (Rozszerzenie funkcji wbudowanej)](../build/reference/ob-inline-function-expansion.md)