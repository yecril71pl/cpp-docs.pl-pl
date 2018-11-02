---
title: Błąd kompilatora C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 8a4a2011124056af7064c8241450e1f3613776a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580872"
---
# <a name="compiler-error-c3073"></a>Błąd kompilatora C3073

"type": klasa ref nie ma konstruktora kopiującego zdefiniowanego przez użytkownika

W [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) kompilacji, kompilator nie wygeneruje konstruktora kopiującego dla typu referencyjnego. W żadnym **/CLR** kompilacji, należy zdefiniować własne konstruktora kopiującego dla typu referencyjnego jeśli oczekujesz, że wystąpienie typu do skopiowania.

Aby uzyskać więcej informacji, zobacz [semantyka stosu C++ dla typów odwołań](../../dotnet/cpp-stack-semantics-for-reference-types.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3073.

```
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```