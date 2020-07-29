---
title: Deklaracje modułów wyliczających języka C
ms.date: 11/04/2016
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
ms.openlocfilehash: d917c93ab8ef2e896f3ef09c9d9191dae49116c3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213726"
---
# <a name="c-enumeration-declarations"></a>Deklaracje modułów wyliczających języka C

Wyliczenie składa się z zestawu nazwanych stałych całkowitych. Deklaracja typu wyliczeniowego zawiera nazwę (opcjonalnie) tag wyliczeniowy i definiuje zestaw nazwanych liczb całkowitych (nazywanych "wyliczeniami", "wyliczającymi", stałymi "" modułami wyliczającymi "lub" składowymi "). Zmienna z typem wyliczenia przechowuje jedną z wartości zestawu wyliczenia zdefiniowanego przez ten typ.

Zmienne **`enum`** typu mogą być używane w wyrażeniach indeksowania oraz jako argumenty operacji wszystkich operatorów arytmetycznych i relacyjnych. Wyliczenia stanowią alternatywę dla `#define` dyrektywy preprocesora, dzięki czemu można generować wartości dla Ciebie i przestrzegać normalnych zasad określania zakresu.

W standardzie ANSI C, wyrażenia definiujące wartość stałej modułu wyliczającego zawsze mają **`int`** Typ; w rezultacie magazyn skojarzony ze zmienną wyliczenia jest magazynem wymaganym dla pojedynczej **`int`** wartości. Stała wyliczenia lub wartość typu wyliczeniowego może być używana wszędzie tam, gdzie język C zezwala na wyrażenie liczby całkowitej.

## <a name="syntax"></a>Składnia

*Wyliczenie — specyfikator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`enum`***identifier*<sub>wybór</sub> **identyfikatora {** *Enumerator-list* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**`enum`***Identyfikator*

*Identyfikator* opcjonalny określa typ wyliczeniowy zdefiniowany przez *moduł wyliczający*. Ten identyfikator jest często nazywany "tagiem" wyliczenia określonego przez listę. Specyfikator typu w formularzu

```
enum identifier
{
    enumerator-list
}
```

deklaruje *Identyfikator* jako tag wyliczenia określonego przez *moduł wyliczający* , który nie jest terminalem listy. *Lista modułów wyliczających* definiuje "zawartość modułu wyliczającego". *Lista modułów wyliczających* została szczegółowo opisana poniżej.

Jeśli deklaracja tagu jest widoczna, kolejne deklaracje używające znacznika, ale pomijania modułów *wyliczających* , określają zadeklarowany wcześniej typ wyliczeniowy. Tag musi odwoływać się do zdefiniowanego typu wyliczenia i ten typ wyliczeniowy musi znajdować się w bieżącym zakresie. Ponieważ typ wyliczenia jest zdefiniowany w innym miejscu, *Lista modułów wyliczających* nie jest wyświetlana w tej deklaracji. Deklaracje typów pochodzących z wyliczeń i **`typedef`** deklaracji dla typów wyliczeniowych mogą użyć znacznika wyliczenia przed zdefiniowaniem typu wyliczenia.

## <a name="syntax"></a>Składnia

*Lista modułów wyliczających*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*liczeni*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*moduł wyliczający — lista* **,** *moduł wyliczający*

*moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Wyliczenie — stała*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wyliczenie — stała* **=** *wyrażenie stałe*

*wyliczenie — stała*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identyfikatora*

Każda *stała wyliczenia* na *liście wyliczenia* określa wartość zestawu wyliczenia. Domyślnie pierwsza *stała Wyliczenie* jest skojarzona z wartością 0. Następna *stała wyliczenia* na liście jest skojarzona z wartością ( *wyrażenie stałe* + 1), chyba że jawnie zostanie skojarzona z inną wartością. Nazwa *stałego wyliczenia* jest równoznaczna z jego wartością.

Aby zastąpić domyślną sekwencję wartości, można użyć *wyliczenia-stała = stała* . W takim przypadku, jeśli *wyliczenie-stała = stała* jest wyświetlana na *liście moduł wyliczający*, *stała wyliczenia* jest skojarzona z wartością podaną przez *wyrażenie stałej*. *Wyrażenie stałe* musi mieć **`int`** Typ i może być ujemne.

Do elementów członkowskich zestawu wyliczania są stosowane następujące reguły:

- Zestaw wyliczenia może zawierać zduplikowane wartości stałych. Można na przykład skojarzyć wartość 0 z dwoma różnymi identyfikatorami, prawdopodobnie nazwanymi `null` i `zero` , w tym samym zestawie.

- Identyfikatory na liście wyliczenia muszą być różne od innych identyfikatorów w tym samym zakresie o tej samej widoczności, w tym zwykłych nazw zmiennych i identyfikatorów na innych listach wyliczenia.

- Tagi wyliczenia przestrzegają normalnych reguł określania zakresu. Muszą one różnić się od innych tagów wyliczenia, struktury i Unii o tej samej widoczności.

## <a name="examples"></a>Przykłady

Te przykłady ilustrują deklaracje wyliczenia:

```
enum DAY            /* Defines an enumeration type    */
{
    saturday,       /* Names day and declares a       */
    sunday = 0,     /* variable named workday with    */
    monday,         /* that type                      */
    tuesday,
    wednesday,      /* wednesday is associated with 3 */
    thursday,
    friday
} workday;
```

Domyślnie jest skojarzona wartość 0 `saturday` . Identyfikator `sunday` jest jawnie ustawiony na 0. Pozostałe identyfikatory domyślnie otrzymują wartości od 1 do 5.

W tym przykładzie wartość z zestawu `DAY` jest przypisana do zmiennej `today` .

```
enum DAY today = wednesday;
```

Należy zauważyć, że nazwa stałej wyliczenia jest używana do przypisywania wartości. Ponieważ `DAY` Typ wyliczeniowy został poprzednio zadeklarowany, konieczne jest tylko oznakowanie wyliczenia `DAY` .

Aby jawnie przypisać wartość całkowitą do zmiennej typu wyliczeniowego, należy użyć rzutowania typu:

```
workday = ( enum DAY ) ( day_value - 1 );
```

To Rzutowanie jest zalecane w języku C, ale nie jest wymagane.

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Tę deklarację można również określić jako

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

lub jako

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Przykład wykorzystujący te zmienne może wyglądać następująco:

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Można również zadeklarować nienazwane typy danych modułu wyliczającego. Nazwa typu danych jest pomijana, ale można zadeklarować zmienne. Zmienna `response` jest zmienną typu zdefiniowanego:

```
enum { yes, no } response;
```

## <a name="see-also"></a>Zobacz także

[Wyliczenia](../cpp/enumerations-cpp.md)
