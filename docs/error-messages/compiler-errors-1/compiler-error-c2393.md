---
title: Błąd kompilatora C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: 39ca693aed3f08e7b2df3d687f94d93384393f23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566858"
---
# <a name="compiler-error-c2393"></a>Błąd kompilatora C2393

> "*symbol*": symbol per-appdomain nie może zostać alokowany w segmencie "*segmentu*"

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Korzystanie z [appdomain](../../cpp/appdomain.md) zmienne oznacza, że kompilujesz z **/CLR: pure** lub **/CLR: Safe**, i bezpieczne lub czysty obraz nie może zawierać segmentów danych.

Zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C2393. Aby rozwiązać ten problem, nie należy tworzyć segmentu danych.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```