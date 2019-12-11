---
title: Błąd narzędzi konsolidatora LNK2033
ms.date: 11/04/2016
f1_keywords:
- LNK2033
helpviewer_keywords:
- LNK2033
ms.assetid: d61db467-9328-4788-bf54-e2a20537f13f
ms.openlocfilehash: 407f5eaf94a0e2da43425c3bbdd1955a88c95f14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991179"
---
# <a name="linker-tools-error-lnk2033"></a>Błąd narzędzi konsolidatora LNK2033

nierozpoznany token TypeRef (token) dla elementu "Type"

Typ nie ma definicji w metadanych MSIL.

LNK2033 może wystąpić podczas kompilowania z **/CLR: Safe** i w przypadku, gdy istnieje tylko Deklaracja do przodu dla typu w module MSIL, gdzie do tego typu odwołuje się moduł MSIL.

Typ musi być zdefiniowany w opcji **/CLR: Safe**.

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje LNK2033.

```cpp
// LNK2033.cpp
// compile with: /clr:safe
// LNK2033 expected
ref class A;
ref class B {};

int main() {
   A ^ aa = nullptr;
   B ^ bb = nullptr;   // OK
};
```
