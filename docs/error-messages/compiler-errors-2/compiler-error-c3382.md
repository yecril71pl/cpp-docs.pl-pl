---
title: Błąd kompilatora C3382
ms.date: 11/04/2016
f1_keywords:
- C3382
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
ms.openlocfilehash: c262ea963ae739fbb76211aae2622e98d5a9b6f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462754"
---
# <a name="compiler-error-c3382"></a>Błąd kompilatora C3382

"sizeof" nie jest obsługiwany z/CLR: Safe

Plik wyjściowy **/CLR: Safe** kompilacja jest plik, który jest weryfikowalny pod kątem bezpieczeństwa typów i sizeof nie jest obsługiwana, ponieważ wartość zwracana przez sizeof operator jest size_t, którego rozmiar różni się zależnie od systemu operacyjnego.

Aby uzyskać więcej informacji, zobacz,

- [sizeof, operator](../../cpp/sizeof-operator.md)

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Typowe problemy przy migracji Visual C++ w wersji 64-bitowej](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3382.

```
// C3382.cpp
// compile with: /clr:safe
int main() {
   sizeof( char );   // C3382
}
```