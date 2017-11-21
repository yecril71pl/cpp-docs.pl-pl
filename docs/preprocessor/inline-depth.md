---
title: inline_depth | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- inline_depth_CPP
- vc-pragma.inline_depth
dev_langs: C++
helpviewer_keywords:
- pragmas, inline_depth
- inline_depth pragma
ms.assetid: 2bba60fe-43ea-4d09-90f7-aafaba3bad07
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7ec052eb387e2dd5ea169b45cdf98edb62f4c203
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="inlinedepth"></a>inline_depth
Określa heurystyki wbudowanego wyszukiwania głębokość, taki sposób, że funkcja nie będzie wbudowanego, jeśli jest przy głębokości (w wykresu wywołań) przekracza `n`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma inline_depth( [n] )  
```  
  
## <a name="remarks"></a>Uwagi  
 Tej pragmy formanty ze śródwierszowaniem funkcji oznaczone [wbudowanego](../cpp/inline-functions-cpp.md) i [__inline](../cpp/inline-functions-cpp.md) lub wbudowanego automatycznie w obszarze opcji/ob2.  
  
 `n`może to być wartość z zakresu od 0 do 255, gdzie 255 oznacza nieograniczoną głębokość wykresu wywołań, a rozszerzenie funkcji wbudowanej powstrzymuje zero.  Gdy `n` nie zostanie określony, używana jest wartość domyślna (254).  
  
 **Inline_depth** pragma Określa, ile razy można rozszerzać szereg wywołania funkcji. Na przykład jeśli głębokość wbudowanego wynosi cztery, a wywołania B, a B C wywołuje, wszystkie trzy wywołania będzie wbudowanego rozwinięte. Jednak najbliższego rozszerzenie funkcji wbudowanej jest dwa, zostaną rozwinięte tylko A i B i C pozostaje jako wywołanie funkcji.  
  
 Aby użyć tej pragmy, musisz ustawić opcję kompilatora /Ob 1 lub 2. Głębokość ustawić za pomocą tej pragmy obowiązuje przy pierwszym wywołaniu funkcji po pragma.  
  
 Głębokość wbudowanego można zmniejszyć podczas rozszerzania, ale nie zwiększa. Jeśli głębokością wbudowany jest sześć i podczas rozszerzania napotka preprocesora **inline_depth** pragma z wartością osiem głębokość pozostaje sześć.  
  
 **Inline_depth** pragma nie ma wpływu na funkcje oznaczone `__forceinline`.  
  
> [!NOTE]
>  Funkcje rekursywne może być wbudowany podstawione maksymalną głębokość wywołań 16.  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [inline_recursion](../preprocessor/inline-recursion.md)