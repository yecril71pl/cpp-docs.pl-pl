---
title: Przegląd deklaracji
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 066c0fd307c7562d70c57c31dff23960a6305f2c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217080"
---
# <a name="overview-of-declarations"></a>Przegląd deklaracji

"Deklaracja" określa interpretację i atrybuty zestawu identyfikatorów. Deklaracja, która również powoduje, że magazyn, który ma być zarezerwowany dla obiektu lub funkcji o nazwie identyfikatora, nazywa się "definicją". Deklaracje języka C dla zmiennych, funkcji i typów mają następującą składnię:

## <a name="syntax"></a>Składnia

*`declaration`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declaration-specifiers`**`attribute-seq`* <sub>opt</sub> *`init-declarator-list`* <sub>opt</sub> opt**`;`**

/\**`attribute-seq`* <sub>wybór</sub> jest niezależny od firmy Microsoft */

*`declaration-specifiers`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`storage-class-specifier`**`declaration-specifiers`* <sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-specifier`**`declaration-specifiers`* <sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`type-qualifier`**`declaration-specifiers`* <sub>wybór</sub>

*`init-declarator-list`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`init-declarator-list`* **`,`** *`init-declarator`*

*`init-declarator`*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*`declarator`* **`=`** *`initializer`*

> [!NOTE]
> Ta składnia *`declaration`* nie jest powtarzana w poniższych sekcjach. Składnia w poniższych sekcjach zwykle zaczyna się od *`declarator`* nieterminalu.

Deklaracje w *`init-declarator-list`* zawiera identyfikatory o nazwie; *`init`* są skrótem dla inicjatora. *`init-declarator-list`* Jest sekwencją rozdzieloną przecinkami deklaratory, z których każdy może zawierać dodatkowe informacje o typie lub inicjatorze lub oba te elementy. *`declarator`* Zawiera identyfikatory, jeśli istnieją, są deklarowane. *`declaration-specifiers`* Nieterminal składa się z sekwencji typów i specyfikatorów klasy magazynowania wskazujących powiązanie, czas trwania magazynu oraz co najmniej część typu jednostek, które Deklaratory. Deklaracje składają się z pewnej kombinacji specyfikatorów klasy magazynowania, specyfikatorów typu, kwalifikatorów typu, Deklaratory i inicjatorów.

Deklaracje mogą zawierać jeden lub więcej atrybutów opcjonalnych wymienionych w *`attribute-seq`* ; *`seq`* jest skrótem sekwencji. Te atrybuty specyficzne dla firmy Microsoft wykonują kilka funkcji, które zostały szczegółowo omówione w tym podręczniku.

W ogólnym formularzu deklaracji zmiennej *`type-specifier`* zwraca typ danych zmiennej. *`type-specifier`* Może być złożonym, tak jak w przypadku, gdy typ jest modyfikowany przez **`const`** lub **`volatile`** . `declarator`Daje nazwę zmiennej, która prawdopodobnie została zmodyfikowana w celu deklarowania tablicy lub typu wskaźnika. Przykład:

```C
int const *fp;
```

deklaruje zmienną o nazwie `fp` jako wskaźnik do niemodyfikowalnej **`const`** wartości () **`int`** . Można zdefiniować więcej niż jedną zmienną w deklaracji przy użyciu wielu deklaratory, rozdzielonych przecinkami.

Deklaracja musi zawierać co najmniej jedną Deklarator lub jego specyfikator typu musi deklarować tag struktury, tag Union lub elementy członkowskie wyliczenia. Deklaratory Podaj wszelkie pozostałe informacje o identyfikatorze. Deklarator jest identyfikatorem, który można zmodyfikować za pomocą nawiasów ( **`[ ]`** ), gwiazdek ( <strong>`*`</strong> ) lub nawiasów ( **`( )`** ), aby zadeklarować odpowiednio tablicę, wskaźnik lub typ funkcji. Gdy deklarujesz proste zmienne (takie jak znaki, liczby całkowite i elementy zmiennoprzecinkowe), lub struktury i związki prostych zmiennych, `declarator` jest to tylko identyfikator. Aby uzyskać więcej informacji na temat deklaratory, zobacz [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md).

Wszystkie definicje są deklaracjami niejawnymi, ale nie wszystkie deklaracje są definicjami. Na przykład deklaracje zmiennych zaczynające się od **`extern`** specyfikatora klasy magazynu to "odwołanie", a nie "Definiowanie" deklaracji. Jeśli zmienna zewnętrzna ma być określona przed zdefiniowaniem lub jeśli jest zdefiniowana w innym pliku źródłowym niż w miejscu, w którym jest używana, **`extern`** wymagana jest deklaracja. Magazyn nie jest przypisywany przez deklaracje "odwołujące się" ani nie można zainicjować zmiennych w deklaracjach.

W deklaracjach zmiennych jest wymagana Klasa magazynu lub typ (lub oba). Z wyjątkiem dla **`__declspec`** , w deklaracji dozwolony jest tylko jeden specyfikator klasy magazynu, a nie wszystkie specyfikatory klasy magazynu są dozwolone w każdym kontekście. **`__declspec`** Klasa magazynu jest dozwolona z innymi specyfikatorami klasy magazynu i jest dozwolona więcej niż raz. Specyfikator klasy magazynowania deklaracji ma wpływ na sposób przechowywania i inicjowania zadeklarowanego elementu oraz tego, które części programu mogą odwoływać się do tego elementu.

*`storage-class-specifier`* Terminale zdefiniowane w C obejmują **`auto`** ,,, **`extern`** **`register`** **`static`** i **`typedef`** . Program Microsoft C zawiera również *`storage-class-specifier`* Terminal **`__declspec`** . Wszystkie *`storage-class-specifier`* terminale z wyjątkiem **`typedef`** i **`__declspec`** są omówione w [klasach magazynu](../c-language/c-storage-classes.md). Aby uzyskać informacje na temat **`typedef`** , zobacz [ `typedef` deklaracje](../c-language/typedef-declarations.md). Aby uzyskać więcej informacji na temat **`__declspec`** , zobacz [atrybuty klasy magazynu rozszerzonego](../c-language/c-extended-storage-class-attributes.md).

Lokalizacja deklaracji w programie źródłowym oraz obecność lub brak innych deklaracji zmiennej są istotnymi czynnikami w celu określenia okresu istnienia zmiennych. Może istnieć wiele ponownych deklaracji, ale tylko jedna definicja. Jednak definicja może być wyświetlana w więcej niż jednej jednostce translacji. W przypadku obiektów z połączeniem wewnętrznym ta reguła ma zastosowanie oddzielnie do każdej jednostki translacji, ponieważ obiekty połączone wewnętrznie są unikatowe dla jednostki tłumaczenia. W przypadku obiektów z powiązaniem zewnętrznym ta reguła ma zastosowanie do całego programu. Aby uzyskać więcej informacji na temat widoczności, zobacz [okres istnienia, zakres, widoczność i powiązania](../c-language/lifetime-scope-visibility-and-linkage.md).

Specyfikatory typów udostępniają pewne informacje o typach danych identyfikatorów. Domyślnym specyfikatorem typu jest **`int`** . Aby uzyskać więcej informacji, zobacz [Specyfikatory typów](../c-language/c-type-specifiers.md). Specyfikatory typu mogą także definiować znaczniki typu, strukturę i nazwy składników Unii oraz stałe wyliczania. Aby uzyskać więcej informacji, zobacz [deklaracje wyliczenia](../c-language/c-enumeration-declarations.md), [deklaracje struktury](../c-language/structure-declarations.md)i [deklaracje Union](../c-language/union-declarations.md).

Istnieją dwa *`type-qualifier`* terminale: **`const`** i **`volatile`** . Kwalifikatory te określają dodatkowe właściwości typów, które są istotne tylko podczas uzyskiwania dostępu do obiektów tego typu przez wartości l. Aby uzyskać więcej informacji na temat **`const`** i **`volatile`** , zobacz [kwalifikatory typów](../c-language/type-qualifiers.md). Aby zapoznać się z definicją l-wartości, zobacz [wyrażenie l-Value i R-Value](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Zobacz też

[Podsumowanie składni języka C](../c-language/c-language-syntax-summary.md)<br/>
[Deklaracje i typy](../c-language/declarations-and-types.md)<br/>
[Podsumowanie deklaracji](../c-language/summary-of-declarations.md)
