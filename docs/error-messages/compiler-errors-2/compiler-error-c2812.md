---
title: Błąd kompilatora C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: 88b071f38cf41db9c929d25ffd526b3f2b7ca468
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62382960"
---
# <a name="compiler-error-c2812"></a>Błąd kompilatora C2812

> \#Import nie jest obsługiwany z/CLR: pure i/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

[#import — dyrektywa](../../preprocessor/hash-import-directive-cpp.md) nie jest obsługiwany przez **/CLR: pure** i **/CLR: Safe** ponieważ `#import` wymaga korzystania z biblioteki obsługi natywnego kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```