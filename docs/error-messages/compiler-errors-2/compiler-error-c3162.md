---
title: Błąd kompilatora C3162 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3162
dev_langs:
- C++
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 529dfa41064e9d22b796b9d079a67b213b816fb2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46030940"
---
# <a name="compiler-error-c3162"></a>Błąd kompilatora C3162

"type": typ odwołania, który ma destruktor nie można użyć jako typu statycznej składowej danych "członek"

Środowisko uruchomieniowe języka wspólnego nie wiedzieć, kiedy trzeba uruchomić destruktor zdefiniowany przez użytkownika, gdy klasa zawiera także funkcja statycznej składowej.

Destruktor nigdy nie zostanie uruchomiony, chyba że obiekt zostanie usunięty w sposób jawny.

Aby uzyskać więcej informacji, zobacz,

- [/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md)

- [Typowe problemy przy migracji Visual C++ w wersji 64-bitowej](../../build/common-visual-cpp-64-bit-migration-issues.md)

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3162.

```
// C3162.cpp
// compile with: /clr /c
ref struct A {
   ~A() { System::Console::WriteLine("in destructor"); }
   static A i;   // C3162
   static A^ a = gcnew A;   // OK
};

int main() {
   A ^ a = gcnew A;
   delete a;
}
```