---
title: Kompilator ostrzeżenie (poziom 4) C4001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4001
dev_langs:
- C++
helpviewer_keywords:
- C4001
ms.assetid: 414a47fe-d597-425e-9374-6a569231dc0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c325656b9e61ee324a3b9f171413f1020440f9ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025415"
---
# <a name="compiler-warning-level-4-c4001"></a>Kompilator ostrzeżenie (poziom 4) C4001

użyto niestandardowego rozszerzenia "single line comment" został użyty.

> [!NOTE]
> To ostrzeżenie jest usuwany w programie Visual Studio 2017 w wersji 15.5, ponieważ Komentarze jednowierszowe są standardowymi C99.

Komentarze jednowierszowe są standardowe w języku C++ i standardu C począwszy od C99.
W obszarze strict zgodność ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), plików języka C, które zawierają Komentarze jednowierszowe Generowanie C4001 z powodu użycia użyto niestandardowego rozszerzenia. Ponieważ Komentarze jednowierszowe standardowego języka C++, C pliki zawierające komentarze jednowierszowe nie tworzą C4001 podczas kompilowania za pomocą rozszerzenia Microsoft (/Ze).

## <a name="example"></a>Przykład

Aby wyłączyć ostrzeżenia, usuń znaczniki komentarza [#pragma warning(disable:4001)](../../preprocessor/warning.md).

```
// C4001.cpp
// compile with: /W4 /Za /TC
// #pragma warning(disable:4001)
int main()
{
   // single-line comment in main
   // C4001
}
```