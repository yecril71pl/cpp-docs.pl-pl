---
title: Błąd kompilatora C2143
ms.date: 11/04/2016
f1_keywords:
- C2143
helpviewer_keywords:
- C2143
ms.assetid: 1d8d1456-e031-4965-9240-09a6e33ba81c
ms.openlocfilehash: 0a7cbad52697ccedac75af73012f6dc69eec5a25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582614"
---
# <a name="compiler-error-c2143"></a>Błąd kompilatora C2143

Błąd składniowy: brakuje "token1" przed "token2"

Kompilator oczekuje określonego tokenu (czyli elementów języka innego niż biały znak), a zamiast tego znaleziono inny token.

Sprawdź [C++ Language Reference](../../cpp/cpp-language-reference.md) ustalenie, gdy kod jest nieprawidłowy. Ponieważ kompilator może zgłosić ten błąd, po napotkaniu wiersza, który powoduje, że ten problem, sprawdź kilka wierszy kodu, które poprzedzają błędu.

C2143 może wystąpić w różnych sytuacjach.

Może wystąpić, gdy operator, który może kwalifikować się nazwę (`::`, `->`, i `.`) musi następować słowo kluczowe `template`, jak w tym przykładzie:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::PutFuncType<Ty, PropTy> // error C2143
    {
    };
};

```

Domyślnie C++ założono, że `Ty::PutFuncType` nie jest szablonem; w związku z tym, że `<` jest interpretowany jako mniej-niż logowania.  Musisz poinformować kompilator jawnie, `PutFuncType` jest szablon, aby go można poprawnie przeanalizować nawiasu ostrego. Aby rozwiązać ten problem, należy użyć `template` słów kluczowych dotyczących nazwy typ zależny, jak pokazano poniżej:

```cpp
class MyClass
{
    template<class Ty, typename PropTy>
    struct PutFuncType : public Ty::template PutFuncType<Ty, PropTy> // correct
    {
    };
};

```

C2143 może wystąpić, gdy **/CLR** jest używany i `using` dyrektywy występuje błąd składni:

```cpp
// C2143a.cpp
// compile with: /clr /c
using namespace System.Reflection;   // C2143
using namespace System::Reflection;
```

Może również wystąpić, próba skompilowania pliku kodu źródłowego za pomocą składni CLR bez również przy użyciu **/CLR**:

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

Pierwszy znak niebędący odstępem, który następuje po `if` instrukcja musi być lewy nawias. Kompilator nie może tłumaczyć czymkolwiek:

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

C2143 może wystąpić, jeśli brak w wierszu, w którym zostanie wykryty błąd zamykającego nawiasu klamrowego, nawiasy lub średnika lub na jeden z wierszy powyżej:

```cpp
// C2143d.cpp
// compile with: /c
class X {
   int member1;
   int member2   // C2143
} x;
```

Lub, jeśli w deklaracji klasy istnieje nieprawidłowy tag:

```cpp
// C2143e.cpp
class X {
   int member;
} x;

class + {};   // C2143 + is an invalid tag name
class ValidName {};   // OK
```

Lub jeśli etykieta nie jest dołączony do instrukcji. Jeśli samodzielnie, należy dodać etykietę, na przykład na końcu instrukcji złożonej, dołącz go do Instrukcja o wartości null:

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

Ten błąd może wystąpić, gdy niekwalifikowanej rozmowy z typem w standardowej bibliotece C++:

```cpp
// C2143g.cpp
// compile with: /EHsc /c
#include <vector>
static vector<char> bad;   // C2143
static std::vector<char> good;   // OK
```

Lub braku przełącznika `typename` — słowo kluczowe:

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

Lub jeśli zostanie podjęta próba zdefiniować jawne utworzenie wystąpienia:

```cpp
// C2143i.cpp
// compile with: /EHsc /c
// template definition
template <class T>
void PrintType(T i, T j) {}

template void PrintType(float i, float j){}   // C2143
template void PrintType(float i, float j);   // OK
```

W programie C zmienne muszą zostać zadeklarowane na początku funkcji i nie może być zadeklarowana po funkcji wykonuje instrukcje-declaration.

```C
// C2143j.c
int main()
{
    int i = 0;
    i++;
    int j = 0; // C2143
}
```
