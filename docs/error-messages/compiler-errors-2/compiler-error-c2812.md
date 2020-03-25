---
title: Błąd kompilatora C2812
ms.date: 11/04/2016
f1_keywords:
- C2812
helpviewer_keywords:
- C2812
ms.assetid: 22aadb8c-7232-489d-a3ad-60662dda30a8
ms.openlocfilehash: cec92982646c64e6c5b669df328e4836d4f44df8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202106"
---
# <a name="compiler-error-c2812"></a>Błąd kompilatora C2812

> \#import nie jest obsługiwany z/CLR: Pure i/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

[dyrektywa #import](../../preprocessor/hash-import-directive-cpp.md) nie jest obsługiwana z **/CLR: Pure** i **/clr: Safe** , ponieważ `#import` wymaga użycia natywnych bibliotek obsługi kompilatora.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2812.

```cpp
// C2812.cpp
// compile with: /clr:pure /c
#import "importlib.tlb"   // C2812
```
