---
title: Błąd kompilatora C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: f91eb428fcb49c81187788730128545916955790
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127663"
---
# <a name="compiler-error-c2059"></a>Błąd kompilatora C2059

Błąd składniowy: "token"

Token spowodował błąd składniowy.

Poniższy przykład generuje komunikat o błędzie dla wiersza, który deklaruje `j`.

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

Aby określić przyczynę błędu, sprawdź nie tylko wiersz, który znajduje się w komunikacie o błędzie, ale również wiersze znajdujące się powyżej. Jeśli badanie wierszy nie daje wskazówki o problemie, spróbuj dodać komentarz do wiersza, który jest wymieniony w komunikacie o błędzie i być może kilka wierszy powyżej.

Jeśli komunikat o błędzie występuje w symbolu, który bezpośrednio następuje po zmiennej `typedef`, upewnij się, że zmienna jest zdefiniowana w kodzie źródłowym.

C2059 jest wywoływane, gdy nazwa symbolu preprocesora jest ponownie używana jako identyfikator. W poniższym przykładzie kompilator widzi `DIGITS.ONE` jako liczbę 1, która nie jest prawidłowa jako nazwa elementu wyliczenia:

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

Możesz uzyskać C2059, jeśli symbol zwróci wartość Nothing, co może wystąpić, gdy **/d**_symbol_ **=** jest używany do kompilowania.

```cpp
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

Innym przypadkiem, w którym może wystąpić C2059, jest Kompilowanie aplikacji, która określa strukturę w domyślnych argumentach dla funkcji. Wartość domyślna argumentu musi być wyrażeniem. Lista inicjalizatora — na przykład, która użyta do zainicjowania struktury — nie jest wyrażeniem.  Aby rozwiązać ten problem, zdefiniuj konstruktora, aby wykonywał wymaganą inicjalizację.

Poniższy przykład generuje C2059:

```cpp
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

C2059 może następować nieprawidłowo sformułowane rzutowanie.

Poniższy przykład generuje C2059:

```cpp
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

C2059 może również wystąpić w przypadku próby utworzenia nazwy przestrzeni nazw zawierającej kropkę.

Poniższy przykład generuje C2059:

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

C2059 może wystąpić, gdy operator, który może kwalifikować się do nazwy (`::`, `->`i `.`), musi następować słowo kluczowe `template`, jak pokazano w tym przykładzie:

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

Domyślnie zakłada się C++ , że `AY::Rebind` nie jest szablonem. w związku z tym następujące `<` są interpretowane jako znak mniejszości.  Musisz powiadomić kompilator jawnie, że `Rebind` jest szablonem, aby mógł prawidłowo przeanalizować nawias ostry. Aby naprawić ten błąd, użyj słowa kluczowego `template` dla nazwy typu zależnego, jak pokazano poniżej:

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
