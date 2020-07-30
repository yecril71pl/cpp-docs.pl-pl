---
title: Błąd kompilatora C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 310083a650f842c6c0f0912efe1ceddb66c4fd6f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214753"
---
# <a name="compiler-error-c2143"></a>Błąd kompilatora C2143

Błąd składniowy: Brak "token1" przed "token2"

Kompilator oczekiwał określonego tokenu (oznacza to, że element języka inny niż biały znak) i zamiast niego znalazł inny token.

Sprawdź [odwołanie do języka C++](../../cpp/cpp-language-reference.md) , aby określić, gdzie kod jest syntaktycznie niepoprawny. Ponieważ kompilator może zgłosić ten błąd po napotkaniu wiersza, który powoduje problem, zaznacz kilka wierszy kodu, które poprzedzają błąd.

C2143 może wystąpić w różnych sytuacjach.

Może wystąpić, gdy operator, który może kwalifikować nazwę ( `::` , `->` i `.` ) musi następować słowo kluczowe **`template`** , jak w poniższym przykładzie:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};
```

Domyślnie C++ zakłada, że `Ty::PutFuncType` nie jest to szablon; w związku z tym następujące `<` jest interpretowane jako znak mniejszości.  Musisz poinformować kompilator jawnie, że `PutFuncType` jest szablonem, aby mógł prawidłowo przeanalizować nawias ostry. Aby naprawić ten błąd, użyj **`template`** słowa kluczowego dla nazwy typu zależnego, jak pokazano poniżej:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};
```

C2143 może wystąpić, gdy jest używany **/CLR** , a **`using`** dyrektywa ma błąd składniowy:

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

Może również wystąpić podczas próby skompilowania pliku kodu źródłowego przy użyciu składni CLR bez użycia **/CLR**:

```cpp
// C2143b.cpp
ref struct A {   // C2143 error compile with /clr
   void Test() {}
};

int main() {
   A a;
   a.Test();
}
```

Pierwszy znak, który nie jest odstępem **`if`** po instrukcji, musi być lewym nawiasem. Kompilator nie może przetłumaczyć żadnych innych elementów:

```cpp
// C2143c.cpp
int main() {
   int j = 0;

   // OK
   if (j < 25)
      ;

   if (j < 25)   // C2143
}
```

C2143 może wystąpić, gdy brakuje zamykającego nawiasu klamrowego, nawiasu lub średnika w wierszu, w którym został wykryty błąd lub jeden z powyższych wierszy:

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

Lub jeśli w deklaracji klasy występuje nieprawidłowy Tag:

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

Lub gdy etykieta nie jest dołączona do instrukcji. Jeśli musisz umieścić etykietę na przykład na końcu złożonej instrukcji, Dołącz ją do instrukcji o wartości null:

```cpp
// C2143f.cpp
// compile with: /c
void func1() {
   // OK
   end1:
      ;

   end2:   // C2143
}
```

Ten błąd może wystąpić, gdy do typu w standardowej bibliotece języka C++ zostanie wykonane niekwalifikowane wywołanie:

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

Lub brak **`typename`** słowa kluczowego:

```cpp
// C2143h.cpp
template <typename T>
struct X {
   struct Y {
      int i;
   };
   Y memFunc();
};
template <typename T>
X<T>::Y X<T>::memFunc() {   // C2143
// try the following line instead
// typename X<T>::Y X<T>::memFunc() {
   return Y();
}
```

Lub jeśli spróbujesz zdefiniować jawne utworzenie wystąpienia:

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

W programie C zmienne muszą być zadeklarowane na początku funkcji i nie mogą być deklarowane po wykonaniu przez funkcję instrukcji niezwiązanych z deklaracją.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
