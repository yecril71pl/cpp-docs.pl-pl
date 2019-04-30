---
title: Compiler Error C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: 6a9568f3c3be88438eae1f28e12dc780301ead0b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402583"
---
# <a name="compiler-error-c3389"></a>Compiler Error C3389

> __declspec (*— słowo kluczowe*) nie może być użyty z/CLR: pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

A [__declspec](../../cpp/declspec.md) używany modyfikator oznacza stan procesu.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) wskazuje na [appdomain](../../cpp/appdomain.md) stanu.  Dlatego deklarowanie zmiennej za pomocą `keyword` **__declspec** modyfikator i kompilowanie za pomocą **/CLR: pure** nie jest dozwolone.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```