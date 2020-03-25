---
title: Ostrzeżenie kompilatora C4956
ms.date: 11/04/2016
f1_keywords:
- C4956
helpviewer_keywords:
- C4956
ms.assetid: 9154f2d1-d49f-4e07-90d2-0e9bc028011a
ms.openlocfilehash: 474bdfa6eb670f39a2876b0c1490e7254cf216e7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164908"
---
# <a name="compiler-warning-c4956"></a>Ostrzeżenie kompilatora C4956

> "*Type*": ten typ nie jest możliwy do zweryfikowania

## <a name="remarks"></a>Uwagi

To ostrzeżenie jest generowane, gdy określono [/CLR: Safe](../../build/reference/clr-common-language-runtime-compilation.md) , a Twój kod zawiera typ, który nie jest możliwy do zweryfikowania. Opcja " **/CLR: Safe** Compiler" jest przestarzała w programie visual Studio 2015 i nie jest obsługiwana w programie visual Studio 2017.

Aby uzyskać więcej informacji, zobacz [czysty i możliwy doC++zweryfikowania kod (/CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

To ostrzeżenie jest wydawane jako błąd i można je wyłączyć za pomocą dyrektywy pragma [Warning](../../preprocessor/warning.md) lub opcji kompilatora [/WD](../../build/reference/compiler-option-warning-level.md) .

## <a name="example"></a>Przykład

Poniższy przykład generuje C4956:

```cpp
// C4956.cpp
// compile with: /clr:safe
int* p;   // C4956
```
