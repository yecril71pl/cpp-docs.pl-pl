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
ms.openlocfilehash: e79ae7f861553ce2bcd7bee6cbb14a3c2965d4ce
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238765"
---
# <a name="scope-c"></a>Zakres (C++)

Deklaracja elementu programu, takich jak klasy, funkcji lub Zmienna nazwy tylko można "odebrane" i używane w niektórych części programu. Kontekst, w którym nazwa jest widoczna jest nazywany jego *zakres*. Na przykład jeśli Zmienna zadeklarowana `x` w funkcji, `x` tylko jest widoczna w tym treści funkcji. Ma ona *zakres lokalny*. Może mieć inne zmienne o takiej samej nazwie w programie; tak długo, jak są one w innych zakresach, narusza reguły jednej definicji, a nie błąd.

Automatyczne zmienne niestatyczna zakres określa także kiedy są tworzone i niszczone w pamięci programu. 

Istnieją sześciu rodzaje zakresu:

- **Globalne** globalną nazwę to taki, który jest zadeklarowana poza klasy, funkcji lub przestrzeni nazw. Jednak w języku C++ nawet te nazwy istnieje z niejawnych globalnej przestrzeni nazw. Zakres nazwy globalne rozciąga się od punkt deklaracji na końcu pliku, w którym jest zadeklarowany. Dla nazwy globalne widoczność podlega również zasady [połączenie](program-and-linkage-cpp.md) określają, czy nazwa jest widoczna w innych plikach w programie.

- **Zakres Namespace** nazwę, która jest zadeklarowana wewnątrz [przestrzeni nazw](namespaces-cpp.md), poza żadnych definicji klasy lub wyliczenia lub bloku funkcji jest widoczny w punkcie deklaracji przestrzeni nazw na końcu. Przestrzeń nazw może być zdefiniowana w blokach wielu różnych plikach.

- **Zakres lokalny** nazwę zadeklarowana wewnątrz funkcji lub lambda, łącznie z nazwami parametru mają zakres lokalny. Są one często nazywane "zmiennych lokalnych". Są one tylko widoczne z ich punkt deklaracji na końcu treści funkcji ani lambda. Zakres lokalny jest rodzajem zakresu bloku, który został omówiony w dalszej części tego artykułu.

- **Klasa zakresu** nazwy elementów członkowskich klasy mają zakres klasy, która rozszerza w definicji klasy niezależnie od punkt deklaracji. Dostępność elementu członkowskiego klasy jest kontrolowane przez dalszego **publicznego**, **prywatnej**, i **chronione** słów kluczowych. Publiczne lub chronione elementy członkowskie jest możliwy tylko za pomocą operatory wyboru elementu członkowskiego (**.** lub **->**) lub operatory wskaźników do elementów członkowskich (**.\***  lub **-> \***).

- **Zakres instrukcji** nazwy zadeklarowany w **dla**, **Jeśli**, **podczas**, lub **przełącznika** instrukcji są widoczne do czasu zakończenia blok instrukcji.

- **Funkcja zakresu** A [etykiety](labeled-statements.md) ma zakres funkcji, co oznacza, jest widoczne w treści funkcji nawet przed jego deklaracji. Zakres funkcji sprawia, że można zapisywać w instrukcjach, takich jak `goto cleanup` przed `cleanup` zadeklarowano etykiety.

## <a name="hiding-names"></a>Ukrywanie nazw

Aby ukryć nazwę, deklarowanie go w zamkniętym bloku. Na poniższej ilustracji `i` jest ponownie zadeklarować w bloku wewnętrznym, a tym samym ukrywanie zmiennej skojarzone z `i` w zakresie bloku zewnętrzne.

 ![Blok&#45;zakres ukrywanie nazwa](../cpp/media/vc38sf1.png "vc38SF1") zakresie bloku i ukrywanie nazwy

 Dane wyjściowe z programu na ilustracji to:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> Argument `szWhat` uważa się w zakresie funkcji. W związku z tym jest traktowana tak, jakby zadeklarowano w najbardziej zewnętrznej bloku funkcji.

## <a name="hiding-class-names"></a>Ukrywanie nazwy klas

 Deklarowanie funkcji, obiektu lub zmienna lub modułu wyliczającego, w tym samym zakresie można ukryć nazwy klasy. Jednak nazwa klasy nadal będą dostępne, gdy poprzedzona słowem kluczowym **klasy**.

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
> Miejsce nazwy klasy (`Account`) jest wywoływana dla klasa — słowo kluczowe musi być używana w odróżnieniu od zmiennej konta globalnego zakresu. Ta zasada nie ma zastosowania w przypadku nazwy klasy po lewej stronie operatora rozpoznawania zakresu (:). Nazwy po lewej stronie operatora rozpoznawanie zakresów zawsze są traktowane jako nazwy klasy.

 W poniższym przykładzie pokazano sposób zadeklarować wskaźnika do obiektu typu `Account` przy użyciu **klasy** — słowo kluczowe:

```cpp
class Account *Checking = new class Account( Account );
```

 `Account` w inicjatorze (w nawiasach) w powyższych instrukcji ma zasięg globalny; jest typu **podwójne**.

> [!NOTE]
> Ponowne użycie nazwy identyfikatora, jak pokazano w poniższym przykładzie jest uważany za niska styl programowania.

 Aby uzyskać więcej informacji na temat wskaźników, zobacz [typów pochodnych](http://msdn.microsoft.com/en-us/aa14183c-02fe-4d81-95fe-beddb0c01c7c). Informacje o deklaracji i inicjowania klasy obiektów, zobacz [klas, struktur i Unii](../cpp/classes-and-structs-cpp.md). Informacji o używaniu **nowe** i **usunąć** magazynu w warstwie bezpłatna operatorów, zobacz [nowy i delete — operatory](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Ukrywanie nazw o zakresie globalnym

 Nazwy globalne można ukryć przez jawne Zadeklarowanie tej samej nazwie w zakresie bloku. Jednak nazwy zakresu globalnego jest możliwy przy użyciu operatora rozpoznawanie zakresów (`::`).

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