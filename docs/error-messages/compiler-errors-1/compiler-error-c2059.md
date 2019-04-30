---
title: Compiler Error C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: 2fb2aa86a1fd8f8e0710d787682fdd44abd941ec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408670"
---
# <a name="compiler-error-c2059"></a>Compiler Error C2059

Błąd składniowy: "token"

Token spowodował błąd składni.

Poniższy przykład generuje komunikat o błędzie dla wiersza, który deklaruje `j`.

```
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Aby ustalić przyczynę tego błędu, sprawdź nie tylko wiersz, który znajduje się w komunikacie o błędzie, ale także linie nad nim. Jeśli badanie wiersze daje nie sugeruje o problemie, spróbuj zakomentowując wiersza, który znajduje się w komunikacie o błędzie i może być kilka wierszy nad nim.

Jeśli komunikat o błędzie pojawia się na symbol, który poprzedza `typedef` zmiennej, upewnij się, że zmienna jest zdefiniowana w kodzie źródłowym.

C2059 jest wywoływane, gdy nazwa symbol preprocesora jest ponownie używane jako identyfikator. W poniższym przykładzie, kompilator będzie widział `DIGITS.ONE` jako numer 1, która jest nieprawidłowa jako nazwa elementu typu wyliczeniowego:

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

C2059 może wystąpić, jeśli symbol daje w wyniku nic, co może mieć miejsce, gdy **/D**_symbol_ **=** jest używana do kompilowania.

```
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

Inny przypadek, w których może wystąpić C2059 jest podczas kompilowania aplikacji, która określa strukturę w domyślne argumenty dla funkcji. Wartość domyślna argumentu musi być wyrażeniem. Lista inicjalizatora — na przykład taki, który jest używany do inicjowania struktury — nie jest wyrażeniem.  Aby rozwiązać ten problem, należy zdefiniować Konstruktor do przeprowadzenia wymaganych inicjowania.

Poniższy przykład generuje C2059:

```
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

C2059 może wystąpić CAST źle sformułowane.

Poniższy przykład spowoduje wygenerowanie C2059:

```
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

C2059 może również wystąpić, jeśli próba utworzenia nazwy przestrzeni nazw, która zawiera znak kropki.

Poniższy przykład spowoduje wygenerowanie C2059:

```
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

C2059 może wystąpić, gdy operator, który może kwalifikować się nazwę (`::`, `->`, i `.`) musi następować słowo kluczowe `template`, jak pokazano w poniższym przykładzie:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

Domyślnie C++ założono, że `AY::Rebind` nie jest szablonem; w związku z tym, że `<` jest interpretowany jako mniej-niż logowania.  Musisz poinformować kompilator jawnie, `Rebind` jest szablon, aby go można poprawnie przeanalizować nawiasu ostrego. Aby rozwiązać ten problem, należy użyć `template` słów kluczowych dotyczących nazwy typ zależny, jak pokazano poniżej:

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
