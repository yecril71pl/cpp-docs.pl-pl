---
title: C3862 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5b21e457feb6d090e4abaf531293987eb3504457
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34704974"
---
# <a name="compiler-error-c3862"></a>C3862 błąd kompilatora

> "*funkcja*": nie można kompilować niezarządzanej funkcji z/CLR: pure lub/CLR: Safe

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Kompilacja z **/CLR: pure** lub **/CLR: Safe** utworzy obraz tylko MSIL obrazu bez natywnego kodu (niezarządzany).  W związku z tym nie można użyć `unmanaged` pragma w **/CLR: pure** lub **/CLR: Safe** kompilacji.

Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) i [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3862:

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```