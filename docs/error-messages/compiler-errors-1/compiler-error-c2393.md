---
title: Błąd kompilatora C2393
ms.date: 11/04/2016
f1_keywords:
- C2393
helpviewer_keywords:
- C2393
ms.assetid: 4bd95728-e813-4ce8-844a-c6ebe235ca82
ms.openlocfilehash: cc3c124f1a4daea0f2517a93c6b354b8233aa5e5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205988"
---
# <a name="compiler-error-c2393"></a>Błąd kompilatora C2393

> "*symbol*": symbol per-AppDomain nie może zostać alokowany*w segmencie segmentu*

## <a name="remarks"></a>Uwagi

**/CLR: Pure** i **/CLR:** opcje kompilatora bezpiecznego są przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017.

Użycie zmiennych [AppDomain](../../cpp/appdomain.md) oznacza, że są kompilowane z **/CLR: Pure** lub **/CLR: Safe**, a Bezpieczny lub czysty obraz nie może zawierać segmentów danych.

Zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md) , aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C2393. Aby rozwiązać ten problem, nie należy tworzyć segmentu danych.

```cpp
// C2393.cpp
// compile with: /clr:pure /c
#pragma data_seg("myseg")
int n = 0;   // C2393
```
