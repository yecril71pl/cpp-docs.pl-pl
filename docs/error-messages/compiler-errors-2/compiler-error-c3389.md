---
title: C3389 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b540f87458c75ddf7d57626b6251248652b96213
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34704308"
---
# <a name="compiler-error-c3389"></a>C3389 błąd kompilatora

> __declspec (*— słowo kluczowe*) nie może być użyty z/CLR: pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

A [__declspec](../../cpp/declspec.md) oznacza modyfikator używane na stan procesu.  [/ CLR: pure](../../build/reference/clr-common-language-runtime-compilation.md) oznacza na [elementu appdomain](../../cpp/appdomain.md) stanu.  Tak, deklarowanie zmiennej o `keyword` **__declspec** modyfikator i kompilowania przy użyciu **/CLR: pure** jest niedozwolone.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3389:

```cpp
// C3389.cpp
// compile with: /clr:pure /c
__declspec(dllexport) int g2 = 0;   // C3389
```