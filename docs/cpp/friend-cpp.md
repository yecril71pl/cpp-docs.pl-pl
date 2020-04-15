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
ms.openlocfilehash: 20116674feffaa5b4bbddf707dd3a4d0c1d9ad98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364444"
---
# <a name="friend-c"></a>friend (C++)

W niektórych okolicznościach jest bardziej wygodne, aby udzielić dostępu na poziomie elementu członkowskiego do funkcji, które nie są członkami klasy lub do wszystkich członków w oddzielnej klasie. Tylko realizator klasy może zadeklarować, kim są jego przyjaciele. Funkcja lub klasa nie może zadeklarować się jako przyjaciel żadnej klasy. W definicji klasy użyj słowa kluczowego **przyjaciela** i nazwy funkcji niebędącej członkiem lub innej klasy, aby udzielić mu dostępu do prywatnych i chronionych członków klasy. W definicji szablonu parametr typu można zadeklarować jako znajomego.

## <a name="syntax"></a>Składnia

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>Deklaracje znajomych

Jeśli deklarujesz funkcję znajomego, która nie została wcześniej zadeklarowana, ta funkcja jest eksportowana do otaczającego zakresu nieklasy.

Funkcje zadeklarowane w deklaracji znajomego są traktowane tak, jakby zostały zadeklarowane przy użyciu słowa kluczowego **extern.** Aby uzyskać więcej informacji, zobacz [extern](extern-cpp.md).

Chociaż funkcje o zakresie globalnym mogą być zadeklarowane jako znajomych przed ich prototypów, funkcje członkowskie nie mogą być zadeklarowane jako znajomych przed pojawieniem się ich deklaracji klasy. Poniższy kod pokazuje, dlaczego to nie powiedzie się:

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

W poprzednim przykładzie wprowadza `ForwardDeclared` nazwę klasy do zakresu, ale pełna deklaracja — `IsAFriend` w szczególności część, która deklaruje funkcję — nie jest znana. W związku z tym `HasFriends` deklaracja **znajomego** w klasie generuje błąd.

Począwszy od języka C++11, istnieją dwie formy deklaracji znajomych dla klasy:

```cpp
friend class F;
friend F;
```

Pierwszy formularz wprowadza nową klasę F, jeśli żadna istniejąca klasa o tej nazwie nie została znaleziona w najbardziej wewnętrznej przestrzeni nazw. **C++11**: Drugi formularz nie wprowadza nowej klasy; może służyć, gdy klasa została już zadeklarowana i musi być używana podczas deklarowania parametru typu szablonu lub typedef jako znajomego.

Użyj, `class friend F` gdy typ, do którego istnieje odwołanie, nie został jeszcze zadeklarowany:

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

W poniższym `friend F` przykładzie odnosi `F` się do klasy, która jest zadeklarowana poza zakresem NS.

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

Służy `friend F` do deklarowania parametru szablonu jako znajomego:

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

Służy `friend F` do deklarowania typedef jako znajomego:

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

Aby zadeklarować dwie klasy, które są przyjaciółmi siebie nawzajem, cała druga klasa musi być określona jako przyjaciel pierwszej klasy. Powodem tego ograniczenia jest to, że kompilator ma wystarczającą ilość informacji do deklarowania funkcji poszczególnych znajomych tylko w punkcie, w którym druga klasa jest zadeklarowana.

> [!NOTE]
> Chociaż cała druga klasa musi być przyjacielem pierwszej klasy, możesz wybrać, które funkcje w pierwszej klasie będą przyjaciółmi drugiej klasy.

## <a name="friend-functions"></a>friend — funkcje

Funkcja **znajomego** jest funkcją, która nie jest członkiem klasy, ale ma dostęp do członków prywatnych i chronionych klasy. Funkcje znajomego nie są uważane za członków klasy; są to normalne funkcje zewnętrzne, które mają specjalne uprawnienia dostępu. Znajomi nie są w zakresie klasy i nie są wywoływane przy użyciu operatorów wyboru członków (**.** i**>**- ), chyba że są członkami innej klasy. Funkcja **znajomego** jest zadeklarowana przez klasę, która udziela dostępu. Deklarację **znajomego** można umieścić w dowolnym miejscu w deklaracji klasy. Nie ma na nie wpływu słowa kluczowe kontroli dostępu.

W poniższym `Point` przykładzie przedstawiono `ChangePrivate`funkcję klasy i znajomego. Funkcja **znajomego** ma dostęp do prywatnego `Point` elementu członkowskiego danych, który otrzymuje jako parametr.

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

## <a name="class-members-as-friends"></a>Członkowie klasy jako przyjaciele

Funkcje członków klasy mogą być zadeklarowane jako znajomych w innych klasach. Rozważmy następujący przykład:

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

W poprzednim przykładzie tylko `A::Func1( B& )` funkcja jest przyznawana `B`friend dostęp do klasy . W związku z tym `_b` dostęp do `Func1` prywatnego `A` elementu `Func2`członkowskiego jest poprawna w klasie, ale nie w .

Klasa `friend` jest klasą, której wszystkie funkcje członkowskie są funkcjami znajomego klasy, czyli których funkcje członkowskie mają dostęp do elementów prywatnych i chronionych członków innej klasy. Załóżmy, że deklaracja `friend` w klasie `B` była:

```cpp
friend class A;
```

W takim przypadku wszystkie funkcje członkowskie w klasie `A` zostałyby przyznane friend dostęp do klasy `B`. Poniższy kod jest przykładem klasy znajomego:

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

Przyjaźń nie jest wzajemna, chyba że wyraźnie określone jako takie. W powyższym przykładzie `YourClass` funkcje członkowskie nie `YourOtherClass`mogą uzyskać dostępu do prywatnych członków programu .

Typ zarządzany (w języku C++/CLI) nie może mieć żadnych funkcji znajomych, klas znajomych ani interfejsów znajomych.

Przyjaźń nie jest dziedziczona, co `YourOtherClass` oznacza, że klasy pochodzące z nie mogą uzyskać dostępu do `YourClass`prywatnych członków. Przyjaźń nie jest przechodnie, więc `YourOtherClass` klasy, które są przyjaciółmi nie może uzyskać dostępu do `YourClass`prywatnych członków.

Na poniższej ilustracji przedstawiono `aFriend`cztery `anotherFriend`deklaracje klas: `Base`, `Derived`, i . Tylko `aFriend` klasa ma bezpośredni dostęp `Base` do prywatnych `Base` członków (i do wszystkich członków, które mogły być dziedziczone).

![Implikacje relacji z przyjaciółmi](../cpp/media/vc38v41.gif "Implikacje relacji z przyjaciółmi") <br/>
Implikacje relacji z przyjaciółmi

## <a name="inline-friend-definitions"></a>Definicje znajomych wbudowanych

Funkcje znajomego można zdefiniować (biorąc pod uwagę treść funkcji) wewnątrz deklaracji klasy. Te funkcje są funkcje wbudowane i podobnie jak funkcje wbudowane elementy członkowskie zachowują się tak, jakby zostały zdefiniowane natychmiast po wszystkich członków klasy zostały widoczne, ale przed zakres klasy jest zamknięty (koniec deklaracji klasy). Funkcje znajomego, które są zdefiniowane wewnątrz deklaracji klasy są w zakresie otaczającej klasy.

## <a name="see-also"></a>Zobacz też

[Słowa kluczowe](../cpp/keywords-cpp.md)
