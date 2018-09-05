---
title: Zakres (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 04/08/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 733d090073fe2ed08a0499ea205c2377b4bdb289
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679700"
---
# <a name="scope-c"></a>Zakres (C++)

Kiedy Deklarujesz element programu, takie jak klasy, funkcji lub zmienna, jego nazwa tylko można "widoczne" i używane w niektórych części programu. Kontekst, w której nazwa jest widoczna jest nazywany jego *zakres*. Na przykład, jeśli zadeklarujemy zmienną `x` w obrębie danej funkcji `x` tylko jest widoczny w obrębie danej treści funkcji. Ma ona *zakres lokalny*. Masz inne zmienne o tej samej nazwie w programach; tak długo, jak są one w różnych zakresach, naruszają reguły jednej definicji, a nie błąd.

Automatycznych zmiennych niestatyczna zakres określa także gdy są tworzone i niszczone w pamięci programu. 

Istnieje sześć rodzaje zakresów:

- **Globalny zakres** globalnej nazwy to taki, który jest zadeklarowana poza klasy, funkcja lub przestrzeni nazw. Jednak w języku C++ nawet tych nazw istnieją przy użyciu niejawnego globalnej przestrzeni nazw. Zakres nazwy globalne rozciąga się od punkt deklaracji na końcu pliku, w którym są one zgłoszone. Dla nazwy globalne widoczność podlegają także reguły [powiązania](program-and-linkage-cpp.md) te określają, czy nazwa jest widoczna w innych plikach w programie.

- **Zakres Namespace** nazwę, która jest zadeklarowana w obrębie [przestrzeni nazw](namespaces-cpp.md), poza żadnych definicji klasy lub typu wyliczeniowego lub bloku funkcji jest widoczna w punkcie deklaracji-to-end w przestrzeni nazw. Przestrzeń nazw może być zdefiniowana w blokach w różnych plikach.

- **Zakres lokalny** nazwy zadeklarowane wewnątrz funkcji lub lambda, łącznie z nazwami parametr mają zakres lokalny. Są one często nazywane "lokalne". Tylko są one widoczne z ich punktu deklarację na końcu treści funkcji lub lambda. Zakres lokalny jest rodzajem zakresu bloku, co zostało omówione w dalszej części tego artykułu.

- **Zakres klasy** nazwy składowych klasy mają zakres klasy, która rozszerza w definicji klasy, niezależnie od tego, punkt deklaracji. Ułatwienia dostępu członków klasy jest kontrolowane przez kolejne **publicznych**, **prywatnej**, i **chronione** słów kluczowych. Publiczne lub chronione elementy członkowskie jest możliwy tylko za pomocą operatory wyboru elementu członkowskiego (**.** lub **->**) lub operatory wskaźników do elementów członkowskich (**.** <strong>\*</strong> lub **->** <strong>\*</strong>).

- **Oświadczenie zakresu** nazwy zadeklarowane w **dla**, **Jeśli**, **podczas**, lub **Przełącz** poufności informacji są widoczne do czasu zakończenia blok instrukcji.

- **Funkcja zakres** A [etykiety](labeled-statements.md) ma zakres funkcji, co oznacza, jest widoczna w treści funkcji, nawet przed jego punkt deklaracji. Zakres funkcji sprawia, że można zapisywać w instrukcjach, takich jak `goto cleanup` przed `cleanup` etykieta jest zadeklarowana.

## <a name="hiding-names"></a>Ukrywanie nazw

Nazwę można ukryć, deklarując go w zamkniętej bloku. Na poniższej ilustracji `i` jest ponownie zadeklarowany w ramach wewnętrznego bloku, w tym samym ukrywanie zmienną związaną z `i` w zakresie zewnętrznym bloku.

 ![Blok&#45;zakresu ukrywaniem nazwy](../cpp/media/vc38sf1.png "vc38SF1") zasięgu bloku i ukrywanie nazw

 Dane wyjściowe programu pokazano na rysunku przedstawiono:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> Argument `szWhat` uznaje się w zakresie funkcji. Dlatego jest ona traktowana tak, jakby była ona zadeklarowana w najbardziej zewnętrznej bloku funkcji.

## <a name="hiding-class-names"></a>Ukrywanie nazw klas

 Aby ukryć nazwy klas, deklarowania funkcji, obiekt lub zmienna lub modułu wyliczającego, w tym samym zakresie. Jednak nazwa klasy jest nadal dostępny przy poprzedzona słowem kluczowym **klasy**.

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

    cout << "Opening account with balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with balance of: 15.37
```

> [!NOTE]
> Miejsce nazwy klasy (`Account`) jest wywoływana dla klasy — słowo kluczowe może służyć do odróżnić go od konta zmiennej zakresu globalnego. Ta zasada nie ma zastosowania w przypadku nazwy klasy po lewej stronie operatora rozpoznawania zakresu (:). Nazwy po lewej stronie operatora rozpoznawania zakresu są zawsze traktowane jako nazwy klas.

 Poniższy przykład pokazuje, jak zadeklarować wskaźnika do obiektu typu `Account` przy użyciu **klasy** — słowo kluczowe:

```cpp
class Account *Checking = new class Account( Account );
```

 `Account` w inicjatorze (w nawiasach) w poprzednich instrukcji się zakresie globalnym; jest on typu **double**.

> [!NOTE]
> Ponowne użycie nazwy identyfikatora, jak pokazano w poniższym przykładzie jest uważany za słabe stylu programowania.

Aby uzyskać informacje na temat deklaracji i inicjowania obiektów klas, zobacz [klas, struktur i Unii](../cpp/classes-and-structs-cpp.md). Informacji o używaniu **nowe** i **Usuń** wolne i sklep z operatorów, zobacz [nowych i delete — operatory](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Ukrywanie nazw o zakresie globalnym

 Aby ukryć nazwy o zakresie globalnym, jawnie Zadeklarowanie tej samej nazwie w zakresie bloku. Jednak nazwy zakresu globalnego jest możliwy za pomocą operatora rozpoznawania zakresu (`::`).

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

## <a name="see-also"></a>Zobacz także
 [Podstawowe pojęcia](../cpp/basic-concepts-cpp.md)