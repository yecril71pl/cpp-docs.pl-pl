---
title: inline_recursion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f3e4ef784d2fcb9ec076d9f8a7c87ffee1d5800
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="inlinerecursion"></a>inline_recursion
Określa rozszerzenie funkcji wbudowanej bezpośrednio lub wzajemnie wywołania funkcji rekursywnych.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma inline_recursion( [{on | off}] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej pragmy do funkcji kontroli oznaczona jako [wbudowanego](../cpp/inline-functions-cpp.md) i [__inline](../cpp/inline-functions-cpp.md) lub funkcje, które kompilator automatycznie rozszerza się w obszarze opcji/ob2. Korzystanie z tej pragmy wymaga [/Ob](../build/reference/ob-inline-function-expansion.md) ustawienia opcji kompilatora 1 lub 2. Stan domyślny dla `inline_recursion` jest wyłączona. Tej pragmy obowiązuje przy pierwszym wywołaniu funkcji po pragma jest widoczna i nie ma wpływu na definicji funkcji.  
  
 `inline_recursion` Pragma kontroluje sposób funkcje rekursywne zostaną rozwinięte. Jeśli `inline_recursion` jest wyłączona, a jeśli wbudowanej funkcji wywołuje sam (bezpośrednio lub pośrednio), funkcję rozszerzonej tylko jeden raz. Jeśli `inline_recursion` jest włączone, funkcja jest rozwinięta wielokrotnie, dopóki nie osiągnie wartość z [inline_depth](../preprocessor/inline-depth.md) pragma, wartością domyślną dla funkcji cyklicznej, które jest definiowana za pomocą `inline_depth` pragma lub pojemności ograniczyć .  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_depth](../preprocessor/inline-depth.md)   
 [/Ob (Rozszerzenie funkcji wbudowanej)](../build/reference/ob-inline-function-expansion.md)