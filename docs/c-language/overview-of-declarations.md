---
title: Przegląd deklaracji
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, about declarations
- type qualifiers
ms.assetid: fcd2364c-c2a5-4fbf-9027-19dac4144cb5
ms.openlocfilehash: 0ffda6522e632533b0aaa4ba146e8fad082ed435
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857063"
---
# <a name="overview-of-declarations"></a>Przegląd deklaracji

"Deklaracja" określa interpretację i atrybuty zestawu identyfikatorów. Deklaracja, która również powoduje, że magazyn, który ma być zarezerwowany dla obiektu lub funkcji o nazwie identyfikatora, nazywa się "definicją". Deklaracje języka C dla zmiennych, funkcji i typów mają następującą składnię:

## <a name="syntax"></a>Składnia

*Deklaracja*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators* *-SEQ*<sub>opt</sub> *init-deklarator-list*<sub>opt</sub>**;**

/\**atrybut-seq*<sub>opt</sub> to specyficzny dla firmy Microsoft */

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja* *specyfikatora klasy magazynu* —<sub>wybór</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *specyfikatora typu* *— wybór specyfikatorów*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;Deklaracja *kwalifikatora typu* *— wybór specyfikatorów*<sub>opt</sub>

*init-deklarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-deklarator-list* **,** *init-deklarator*

*init-deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *inicjator* deklarator

> [!NOTE]
> Ta składnia *deklaracji* nie jest powtarzana w poniższych sekcjach. Składnia w poniższych sekcjach zwykle zaczyna się od *deklarator* nieterminalu.

Deklaracje w *init-deklarator-list* zawierają identyfikatory o nazwie; *init* jest skrótem inicjatora. *Init-deklarator-list* to rozdzielona przecinkami sekwencja deklaratory, z których każdy może zawierać dodatkowe informacje o typie lub inicjatorze lub oba te elementy. *Deklarator* zawiera identyfikatory (jeśli istnieją), które są zadeklarowane. *Deklaracje specyfikatorów* nieterminalu składają się z sekwencji typu i specyfikator klasy magazynu, które wskazują powiązanie, czas trwania magazynu i co najmniej część typu jednostek, które Deklaratory. W związku z tym deklaracje składają się z pewnej kombinacji specyfikatorów klasy magazynowania, specyfikatorów typu, kwalifikatorów typu, Deklaratory i inicjatorów.

Deklaracje mogą zawierać jeden lub więcej atrybutów opcjonalnych wymienionych w *atrybucie-SEQ*; *SEQ* jest skrótem sekwencji. Te atrybuty specyficzne dla firmy Microsoft wykonują szereg funkcji, które są szczegółowo omówione w tym podręczniku.

W ogólnym formularzu deklaracji zmiennej, *specyfikator typu* zwraca typ danych zmiennej. *Specyfikator typu* może być złożonym, tak jakby typ został zmodyfikowany przez **stałą** lub `volatile`. `declarator` Daje nazwę zmiennej, która prawdopodobnie została zmodyfikowana w celu deklarowania tablicy lub typu wskaźnika. Na przykład:

```C
int const *fp;
```

deklaruje zmienną o `fp` nazwie jako wskaźnik do niemodyfikowalnej wartości**const**(const `int` ). Można zdefiniować więcej niż jedną zmienną w deklaracji przy użyciu wielu deklaratory, rozdzielonych przecinkami.

Deklaracja musi zawierać co najmniej jedną Deklarator lub jego specyfikator typu musi deklarować tag struktury, tag Union lub elementy członkowskie wyliczenia. Deklaratory Podaj wszelkie pozostałe informacje o identyfikatorze. Deklarator jest identyfikatorem, który można zmodyfikować za pomocą nawiasów kwadratowych (**[]**), gwiazdek<strong>\*</strong>() lub nawiasów ( **()** ), aby zadeklarować odpowiednio tablicę, wskaźnik lub typ funkcji. Gdy deklarujesz proste zmienne (takie jak znaki, liczby całkowite i elementy zmiennoprzecinkowe), lub struktury i związki prostych zmiennych, `declarator` jest to tylko identyfikator. Aby uzyskać więcej informacji na temat deklaratory, zobacz [Deklaratory i deklaracje zmiennych](../c-language/declarators-and-variable-declarations.md).

Wszystkie definicje są deklaracjami niejawnymi, ale nie wszystkie deklaracje są definicjami. Na przykład deklaracje zmiennych zaczynające się od `extern` specyfikatora klasy magazynu to "odwołanie", a nie "Definiowanie" deklaracji. Jeśli zmienna zewnętrzna ma być określona przed zdefiniowaniem lub jeśli jest zdefiniowana w innym pliku źródłowym niż ten, w którym jest używana, wymagana jest `extern` deklaracja. Magazyn nie jest przypisywany przez deklaracje "odwołujące się" ani nie można zainicjować zmiennych w deklaracjach.

W deklaracjach zmiennych jest wymagana Klasa magazynu lub typ (lub oba). Z wyjątkiem `__declspec`dla, w deklaracji dozwolony jest tylko jeden specyfikator klasy magazynu, a nie wszystkie specyfikatory klasy magazynu są dozwolone w każdym kontekście. Klasa `__declspec` magazynu jest dozwolona z innymi specyfikatorami klasy magazynu i jest dozwolona więcej niż raz. Specyfikator klasy magazynowania deklaracji ma wpływ na sposób przechowywania i inicjowania zadeklarowanego elementu oraz tego, które części programu mogą odwoływać się do tego elementu.

Terminale *specyfikatora klasy magazynowania* zdefiniowane w C obejmują **funkcję**Auto, `extern`, **register**, **static**i `typedef`. Ponadto program Microsoft C zawiera Terminal `__declspec` *klasy magazynu specyfikatora* . Wszystkie terminale *klasy magazynu specyfikatorów* z wyjątkiem `typedef` i `__declspec` są omówione w [klasach magazynu](../c-language/c-storage-classes.md). Zobacz [deklaracje typedef](../c-language/typedef-declarations.md) , aby `typedef`uzyskać informacje o. Zobacz [rozszerzone atrybuty klasy magazynu](../c-language/c-extended-storage-class-attributes.md) , aby uzyskać informacje `__declspec`o programie.

Lokalizacja deklaracji w programie źródłowym oraz obecność lub brak innych deklaracji zmiennej są istotnymi czynnikami w celu określenia okresu istnienia zmiennych. Może istnieć wiele ponownych deklaracji, ale tylko jedna definicja. Jednak definicja może być wyświetlana w więcej niż jednej jednostce translacji. W przypadku obiektów z połączeniem wewnętrznym ta reguła ma zastosowanie oddzielnie do każdej jednostki translacji, ponieważ obiekty połączone wewnętrznie są unikatowe dla jednostki tłumaczenia. W przypadku obiektów z powiązaniem zewnętrznym ta reguła ma zastosowanie do całego programu. Zobacz [okres istnienia, zakres, widoczność i połączenie,](../c-language/lifetime-scope-visibility-and-linkage.md) Aby uzyskać więcej informacji na temat widoczności.

Specyfikatory typów udostępniają pewne informacje o typach danych identyfikatorów. Domyślnym specyfikatorem typu jest `int`. Aby uzyskać więcej informacji, zobacz [Specyfikatory typów](../c-language/c-type-specifiers.md). Specyfikatory typu mogą także definiować znaczniki typu, strukturę i nazwy składników Unii oraz stałe wyliczania. Aby uzyskać więcej informacji, zobacz [deklaracje wyliczenia](../c-language/c-enumeration-declarations.md), [deklaracje struktury](../c-language/structure-declarations.md)i [deklaracje Union](../c-language/union-declarations.md).

Istnieją dwa zaciski *kwalifikatorów typu* : **const** i `volatile`. Kwalifikatory te określają dodatkowe właściwości typów, które są istotne tylko podczas uzyskiwania dostępu do obiektów tego typu przez wartości l. Aby uzyskać więcej informacji **const** na temat `volatile`const i, zobacz [kwalifikatory typów](../c-language/type-qualifiers.md). Aby zapoznać się z definicją l-wartości, zobacz [wyrażenie l-Value i R-Value](../c-language/l-value-and-r-value-expressions.md).

## <a name="see-also"></a>Zobacz też

[Podsumowanie składni języka C](../c-language/c-language-syntax-summary.md)<br/>
[Deklaracje i typy](../c-language/declarations-and-types.md)<br/>
[Podsumowanie deklaracji](../c-language/summary-of-declarations.md)
