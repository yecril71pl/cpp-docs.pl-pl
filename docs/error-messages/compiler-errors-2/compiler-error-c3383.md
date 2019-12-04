---
title: Błąd kompilatora C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: ceae17689cbcb9585fb3722580042187ff64a6ee
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755632"
---
# <a name="compiler-error-c3383"></a>Błąd kompilatora C3383

element "operator new" nie jest obsługiwany z/CLR: Safe

Plik wyjściowy **/CLR: Safe** kompilacja jest plikiem, który jest typu "bezpieczna", a wskaźniki nie są obsługiwane.

Aby uzyskać więcej informacji, zobacz,

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Typowe problemy przy migracji Visual C++ w wersji 64-bitowej](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Przykład

Poniższy przykład generuje C3383.

```cpp
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```
