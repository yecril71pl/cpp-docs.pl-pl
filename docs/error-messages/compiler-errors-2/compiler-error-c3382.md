---
title: Błąd kompilatora C3382 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3382
dev_langs:
- C++
helpviewer_keywords:
- C3382
ms.assetid: a7603abd-ac4e-4ae6-a02b-3bdc6d1908a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6da27531b95950a12cb9aa95e8e89da94c556d2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035966"
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