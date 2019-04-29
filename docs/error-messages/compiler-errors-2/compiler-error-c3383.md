---
title: Błąd kompilatora C3383
ms.date: 11/04/2016
f1_keywords:
- C3383
helpviewer_keywords:
- C3383
ms.assetid: ceb7f725-f417-4dc3-8496-0f413bb76687
ms.openlocfilehash: 38aea188eeac90cd23d9203a53b4e630be2f115b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367346"
---
# <a name="compiler-error-c3383"></a>Błąd kompilatora C3383

"operator new" nie jest obsługiwany z/CLR: Safe

Plik wyjściowy **/CLR: Safe** kompilacja jest plik, który jest weryfikowalny pod kątem bezpieczeństwa typów i wskaźniki nie są obsługiwane.

Aby uzyskać więcej informacji, zobacz,

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Typowe problemy przy migracji Visual C++ w wersji 64-bitowej](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3383.

```
// C3383.cpp
// compile with: /clr:safe
int main() {
   char* pCharArray = new char[256];  // C3383
}
```