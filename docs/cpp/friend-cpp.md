---
title: friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 772eada8257917a6127b15ea2e50946aebb3bc74
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227468"
---
# <a name="friend-c"></a>friend (C++)

W niektórych sytuacjach wygodniejsze jest przyznanie dostępu na poziomie elementu członkowskiego do funkcji, które nie są członkami klasy ani do wszystkich elementów członkowskich w oddzielnym klasie. Tylko implementujący Klasa może zadeklarować, kto jest jego znajomych. Funkcja lub Klasa nie można zadeklarować siebie jako zaprzyjaźnionej z jakąkolwiek klasą. W definicji klasy należy użyć **`friend`** słowa kluczowego i nazwy funkcji nieczłonkowskiej lub innej klasy w celu udzielenia jej dostępu do prywatnych i chronionych elementów członkowskich klasy. W definicji szablonu parametr typu może być zadeklarowany jako zaprzyjaźniony.

## <a name="syntax"></a>Składnia

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Deklaracje zaprzyjaźnione

Jeśli zadeklarujesz funkcję zaprzyjaźnioną, która nie została wcześniej zadeklarowana, ta funkcja jest eksportowana do otaczającego zakresu nieklasowego.

Funkcje zadeklarowane w deklaracji zaprzyjaźnionej są traktowane tak, jakby zostały zadeklarowane za pomocą **`extern`** słowa kluczowego. Aby uzyskać więcej informacji, zobacz [extern](extern-cpp.md).

Chociaż funkcje z zakresem globalnym można zadeklarować jako znajomych przed ich prototypami, funkcje składowe nie mogą być deklarowane jako zaprzyjaźnione przed wyglądem kompletnej deklaracji klasy. Poniższy kod przedstawia przyczynę niepowodzenia:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

Poprzedni przykład wprowadza nazwę klasy `ForwardDeclared` do zakresu, ale kompletną deklarację — w tym, część, która deklaruje funkcję `IsAFriend` — jest nieznana. W związku z tym **`friend`** Deklaracja w klasie `HasFriends` generuje błąd.

Począwszy od języka C++ 11, istnieją dwie formy deklaracji zaprzyjaźnionych dla klasy:

```cpp
friend class F;
friend F;
```

W pierwszym formularzu wprowadzono nową klasę F, jeśli żadna istniejąca Klasa o tej nazwie nie została znaleziona w wewnętrznej przestrzeni nazw. **C++ 11**: drugi formularz nie wprowadza nowej klasy; można go użyć, gdy klasa została już zadeklarowana, i musi być użyta podczas deklarowania parametru typu szablonu lub elementu typedef jako przyjaciela.

Użyj `class friend F` , gdy przywoływany typ nie został jeszcze zadeklarowany:

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

W poniższym przykładzie `friend F` odwołuje się do `F` klasy, która jest zadeklarowana poza zakresem NS.

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

Użyj `friend F` , aby zadeklarować parametr szablonu jako zaprzyjaźniony:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Użyj, `friend F` Aby zadeklarować element typedef jako zaprzyjaźniony:

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Aby zadeklarować dwie klasy, które są znajomych ze sobą, cała druga Klasa musi być określona jako osoba zaprzyjaźniona pierwszej klasy. Przyczyną tego ograniczenia jest fakt, że kompilator ma wystarczającą ilość informacji, aby zadeklarować poszczególne funkcje zaprzyjaźnione tylko w punkcie, w którym jest zadeklarowana druga Klasa.

> [!NOTE]
> Chociaż cała druga Klasa musi być zaprzyjaźniona z pierwszą klasą, można wybrać funkcje w pierwszej klasie, które będą przyjaciółmi drugiej klasy.

## <a name="friend-functions"></a>friend — funkcje

**`friend`** Funkcja jest funkcją, która nie jest elementem członkowskim klasy, ale ma dostęp do prywatnych i chronionych elementów członkowskich klasy. Funkcje zaprzyjaźnione nie są uznawane za składowe klasy; są one normalnymi funkcjami zewnętrznymi, które mają specjalne uprawnienia dostępu. Przyjaciele nie znajdują się w zakresie klasy i nie są wywoływane przy użyciu operatorów wyboru elementu członkowskiego (**.** i- **>** ), chyba że są członkami innej klasy. **`friend`** Funkcja jest zadeklarowana przez klasę, która udziela dostępu. **`friend`** Deklarację można umieścić w dowolnym miejscu w deklaracji klasy. Słowa kluczowe kontroli dostępu nie mają na nie wpływ.

Poniższy przykład pokazuje `Point` klasę i funkcję zaprzyjaźnioną, `ChangePrivate` . **`friend`** Funkcja ma dostęp do prywatnego elementu członkowskiego danych obiektu, który `Point` odbiera jako parametr.

```cpp
// friend_functions.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
    friend void ChangePrivate( Point & );
public:
    Point( void ) : m_i(0) {}
    void PrintPrivate( void ){cout << m_i << endl; }

private:
    int m_i;
};

void ChangePrivate ( Point &i ) { i.m_i++; }

int main()
{
   Point sPoint;
   sPoint.PrintPrivate();
   ChangePrivate(sPoint);
   sPoint.PrintPrivate();
// Output: 0
           1
}
```

## <a name="class-members-as-friends"></a>Składowe klas jako znajomych

Funkcje składowe klasy mogą być deklarowane jako zaprzyjaźnione w innych klasach. Rozpatrzmy następujący przykład:

```cpp
// classes_as_friends1.cpp
// compile with: /c
class B;

class A {
public:
   int Func1( B& b );

private:
   int Func2( B& b );
};

class B {
private:
   int _b;

   // A::Func1 is a friend function to class B
   // so A::Func1 has access to all members of B
   friend int A::Func1( B& );
};

int A::Func1( B& b ) { return b._b; }   // OK
int A::Func2( B& b ) { return b._b; }   // C2248
```

W poprzednim przykładzie tylko funkcja `A::Func1( B& )` ma udzielony dostęp do klasy `B` . W związku z tym dostęp do prywatnego elementu członkowskiego `_b` jest poprawny w `Func1` klasie, `A` ale nie w `Func2` .

**`friend`** Klasa jest klasą, której wszystkie funkcje składowe są zaprzyjaźnionymi funkcjami klasy, czyli, których elementy członkowskie mają dostęp do prywatnych i chronionych elementów członkowskich klasy. Załóżmy, że **`friend`** Deklaracja w klasie `B` była:

```cpp
friend class A;
```

W takim przypadku wszystkie funkcje składowe w klasie `A` byłyby przyznane znajomemu dostępowi do klasy `B` . Poniższy kod jest przykładem klasy zaprzyjaźnionej:

```cpp
// classes_as_friends2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class YourClass {
friend class YourOtherClass;  // Declare a friend class
public:
   YourClass() : topSecret(0){}
   void printMember() { cout << topSecret << endl; }
private:
   int topSecret;
};

class YourOtherClass {
public:
   void change( YourClass& yc, int x ){yc.topSecret = x;}
};

int main() {
   YourClass yc1;
   YourOtherClass yoc1;
   yc1.printMember();
   yoc1.change( yc1, 5 );
   yc1.printMember();
}
```

Przyjaźń nie jest wzajemna, chyba że wyraźnie określono jako takie. W powyższym przykładzie funkcja członkowska `YourClass` nie może uzyskać dostępu do prywatnych członków `YourOtherClass` .

Typ zarządzany (w języku C++/CLI) nie może mieć żadnych zaprzyjaźnionych funkcji, zaprzyjaźnionych klas ani interfejsów zaprzyjaźnionych.

Przyjaźń nie jest dziedziczona, co oznacza, że klasy pochodzące od `YourOtherClass` nie mogą uzyskać dostępu do `YourClass` prywatnych członków. Przyjaźń nie jest przechodnia, dlatego klasy, które są znajomymi `YourOtherClass` nie mogą uzyskać dostępu do `YourClass` prywatnych członków.

Na poniższej ilustracji przedstawiono cztery deklaracje klasy: `Base` ,, `Derived` `aFriend` , i `anotherFriend` . Tylko Klasa `aFriend` ma bezpośredni dostęp do prywatnych elementów członkowskich `Base` (i do wszystkich elementów członkowskich, które `Base` mogą mieć Odziedziczone).

![Implikacje relacji zaprzyjaźnionej](../cpp/media/vc38v41.gif "Implikacje relacji zaprzyjaźnionej") <br/>
Implikacje relacji zaprzyjaźnionej

## <a name="inline-friend-definitions"></a>Wbudowane definicje zaprzyjaźnione

Funkcje zaprzyjaźnione mogą być zdefiniowane (w treści funkcji) wewnątrz deklaracji klasy. Te funkcje są funkcjami wbudowanymi, podobnie jak funkcje wbudowanego elementu członkowskiego, tak jakby były zdefiniowane bezpośrednio po dodaniu wszystkich elementów członkowskich klasy, ale przed zamknięciem zakresu klasy (koniec deklaracji klasy). Zaprzyjaźnione funkcje, które są zdefiniowane wewnątrz deklaracji klasy, znajdują się w zakresie otaczającej klasy.

## <a name="see-also"></a>Zobacz także

[Słowa kluczowe](../cpp/keywords-cpp.md)
