---
title: Błąd kompilatora C3389
ms.date: 11/04/2016
f1_keywords:
- C3389
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
ms.openlocfilehash: b166096390169939f01bcb976a57612f10f7df2e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201139"
---
# <a name="compiler-error-c3389"></a>Błąd kompilatora C3389

> nie można użyć __declspec (*słowo kluczowe*) z/CLR: Pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Użyty modyfikator [__declspec](../../cpp/declspec.md) oznacza stan na proces.  [/CLR: Pure](../../build/reference/clr-common-language-runtime-compilation.md) oznacza stan [domeny aplikacji](../../cpp/appdomain.md) .  Dlatego zadeklarowanie zmiennej z modyfikatorem **__declspec** `keyword`i kompilowanie za pomocą **/CLR: Pure** jest niedozwolone.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```
