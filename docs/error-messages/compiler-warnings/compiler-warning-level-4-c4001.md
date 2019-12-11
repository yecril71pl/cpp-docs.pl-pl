---
title: Ostrzeżenie kompilatora (poziom 4) C4001
ms.date: 11/04/2016
f1_keywords:
- C4001
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
ms.openlocfilehash: ceb7e65a292e5b9e9ef960ca9553183b703c93f0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991686"
---
# <a name="compiler-warning-level-4-c4001"></a>Ostrzeżenie kompilatora (poziom 4) C4001

użyto niestandardowego rozszerzenia "Single line Comment"

> [!NOTE]
> To ostrzeżenie jest usuwane w programie Visual Studio 2017 w wersji 15,5, ponieważ Komentarze jednowierszowe są standardowe w C99.

Komentarze jednowierszowe są standardowymi C++ wersjami w języku C, począwszy od C99.
W obszarze ścisła zgodność ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)), pliki języka C, które zawierają jednowierszowe komentarze, generują C4001 z powodu użycia niestandardowego rozszerzenia. Ze względu na to, że komentarze C++jednowierszowe są standardami w, pliki C zawierające Komentarze jednowierszowe nie generują C4001 podczas kompilowania z rozszerzeniami Microsoft (/ze).

## <a name="example"></a>Przykład

Aby wyłączyć ostrzeżenie, Usuń komentarz [#pragma ostrzeżenie (Wyłącz: 4001)](../../preprocessor/warning.md).

```cpp
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```
