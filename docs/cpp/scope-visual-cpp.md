---
title: Zakres (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: a5b5601c89991fbe1a148ebaf781fe2ad6a9dfc4
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83204139"
---
# <a name="scope-c"></a>Zakres (C++)

W przypadku deklarowania elementu programu, takiego jak Klasa, funkcja lub zmienna, jego nazwa może być "widoczna" i używana w niektórych częściach programu. Kontekst, w którym nazwa jest widoczna, nazywa się jego *zakresem*. Na przykład, Jeśli deklarujesz zmienną `x` w funkcji, `x` jest widoczna tylko w tej treści funkcji. Ma *zakres lokalny*. W programie mogą istnieć inne zmienne o tej samej nazwie. o ile znajdują się w różnych zakresach, nie naruszają one jednej reguły definicji i nie zostanie zgłoszony błąd.

W przypadku automatycznych zmiennych niestatycznych zakres określa również, kiedy są tworzone i niszczone w pamięci programu.

Istnieje sześć rodzajów zakresu:

- **Zakres globalny** Globalna nazwa jest taka, która jest zadeklarowana poza jakąkolwiek klasą, funkcją lub przestrzenią nazw. Jednak w języku C++ nawet te nazwy istnieją z niejawną globalną przestrzenią nazw. Zakres nazw globalnych rozciąga się od punktu deklaracji do końca pliku, w którym są zadeklarowane. W przypadku nazw globalnych widoczność jest również regulowana regułami [powiązania](program-and-linkage-cpp.md) , które określają, czy nazwa jest widoczna w innych plikach w programie.

- **Zakres przestrzeni nazw** Nazwa, która jest zadeklarowana w [przestrzeni nazw](namespaces-cpp.md), poza klasą lub definicją typu enum lub blok funkcji, jest widoczna w punkcie deklaracji na końcu przestrzeni nazw. Przestrzeń nazw może być zdefiniowana w wielu blokach w różnych plikach.

- **Zakres lokalny** Nazwa zadeklarowana wewnątrz funkcji lub wyrażenia lambda, łącznie z nazwami parametrów, mają zakres lokalny. Są one często określane jako "locale". Są one widoczne tylko w punkcie deklaracji na końcu funkcji lub treści lambda. Zakres lokalny to rodzaj zakresu blokowego, który został omówiony w dalszej części tego artykułu.

- **Zakres klasy** Nazwy elementów członkowskich klasy mają zakres klasy, który rozciąga się w całej definicji klasy niezależnie od punktu deklaracji. Ułatwienia dostępu składowej klasy są dodatkowo kontrolowane przez **publiczne**, **prywatne**i **chronione** słowa kluczowe. Dostęp do publicznych lub chronionych składowych można uzyskać tylko przy użyciu operatorów wyboru elementu członkowskiego (**.** or **->** ) lub operatory wskaźnika do składowej (**.** <strong>\*</strong> lub **->** <strong>\*</strong> ).

- **Zakres instrukcji** Nazwy zadeklarowane w instrukcji **for**, **if**, **while**lub **Switch** są widoczne do końca bloku instrukcji.

- **Zakres funkcji** [Etykieta](labeled-statements.md) ma zakres funkcji, co oznacza, że jest widoczna w całej treści funkcji nawet przed punktem deklaracji. Zakres funkcji umożliwia pisanie instrukcji, takich jak `goto cleanup` przed `cleanup` zadeklarowaniem etykiety.

## <a name="hiding-names"></a>Ukrywanie nazw

Nazwę można ukryć, deklarując ją w załączonym bloku. Na poniższym rysunku, `i` jest ponownie zadeklarowany w bloku wewnętrznym, ukrywając zmienną skojarzoną z `i` w zewnętrznym zakresie bloku.

![Blokuj ukrywanie nazwy zakresu&#45;](../cpp/media/vc38sf1.png "Blokuj ukrywanie nazwy zakresu&#45;") <br/>
Ukrywanie zakresu i nazwy bloku

Dane wyjściowe programu pokazane na rysunku są następujące:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> Argument `szWhat` jest uznawany za w zakresie funkcji. W związku z tym jest traktowany tak, jakby był zadeklarowany w najbardziej zewnętrznym bloku funkcji.

## <a name="hiding-class-names"></a>Ukrywanie nazw klas

Nazwy klas można ukryć, deklarując funkcję, obiekt lub zmienną lub moduł wyliczający w tym samym zakresie. Jednak nazwy klasy nadal można uzyskać przy użyciu prefiksu **klasy**słowa kluczowego.

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as
                                       //  class name

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> W każdym miejscu jest wywoływana nazwa klasy ( `Account` ) dla, Klasa słowo kluczowe musi być używana w celu odróżnienia go od konta zmiennej o zakresie globalnym. Ta zasada nie ma zastosowania, gdy nazwa klasy występuje po lewej stronie operatora rozpoznawania zakresu (::). Nazwy po lewej stronie operatora rozpoznawania zakresu są zawsze uznawane za nazwy klas.

Poniższy przykład ilustruje sposób deklarowania wskaźnika do obiektu typu `Account` za pomocą słowa kluczowego **Class** :

```cpp
class Account *Checking = new class Account( Account );
```

`Account`Element w inicjatorze (w nawiasach) w powyższej instrukcji ma zakres globalny; jest to typ **Double**.

> [!NOTE]
> Wielokrotne użycie nazw identyfikatorów, jak pokazano w tym przykładzie, jest uznawane za słaby styl programowania.

Aby uzyskać informacje na temat deklaracji i inicjalizacji obiektów klasy, zobacz [klasy, struktury i związki](../cpp/classes-and-structs-cpp.md). Aby uzyskać informacje na temat korzystania z operatorów **New** i **delete** Free-Store, zobacz [New and DELETE Operators](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Ukrywanie nazw z zakresem globalnym

Można ukryć nazwy z zakresem globalnym, jawnie deklarując tę samą nazwę w zakresie bloku. Jednak nazwy zakresu globalnego można uzyskać za pomocą operatora rozpoznawania zakresu ( `::` ).

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>Zobacz też

[Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)
