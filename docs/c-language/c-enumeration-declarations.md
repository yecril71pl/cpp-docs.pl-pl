---
title: Deklaracje modułów Wyliczających języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declarations, enumerations
- define directive (#define), alternative to
- enumerators, declaring
- '#define directive, alternative to'
- named constants, enumeration declarations
- declaring enumerations
ms.assetid: bd18f673-4dda-4bc1-92fd-d1ce10074910
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 858f7bf440b0a53a7e9ed5bb666029b7d1135f81
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091897"
---
# <a name="c-enumeration-declarations"></a>Deklaracje modułów wyliczających języka C

Wyliczenie składa się z zestawu stałe całkowite nazwanych. Deklaracja typu wyliczenia nadaje nazwę tagu (opcjonalne) wyliczenie i definiuje zestaw o nazwie całkowitą identyfikatory (nazywane "wyliczenie zestawem," "stałe modułu wyliczającego", "moduły wyliczające" lub "Członkowie"). Zmienna typu wyliczenia przechowuje jedną z wartości zestawu wyliczenie, określonego przez tego typu.

Zmienne `enum` typu można używać w wyrażeniach indeksowania i jako argumentów wszystkich operatorów arytmetycznych. Wyliczenia alternatywną `#define` dyrektywy preprocesora z korzyściami, że wartości mogą być generowane automatycznie i przestrzegają normalne reguły określania zakresów.

W ANSI C wyrażeń, które określają wartości stałej modułu wyliczającego zawsze mieć `int` typ; w związku z tym, Magazyn skojarzony ze zmienną wyliczenia jest magazynu wymaganego dla pojedynczego `int` wartość. Stała lub wartość wyliczenia typu mogą być używane wszędzie język C umożliwia wyrażeniem liczby całkowitej.

## <a name="syntax"></a>Składnia

*Specyfikator typu wyliczeniowego*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wyliczenie** *identyfikator*<sub>zoptymalizowany pod kątem</sub> **{** *lista_modułów_wyliczających* **}**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**wyliczenie** *identyfikator*

Opcjonalny *identyfikator* nazwy typu wyliczenia zdefiniowanych przez *lista_modułów_wyliczających*. Ten identyfikator jest często określany mianem "tag" wyliczenie określone przez listę. Specyfikator typu formularza

```
enum identifier
{
    enumerator-list
}
```

deklaruje *identyfikator* zostaną tag wyliczenia określony przez *lista_modułów_wyliczających* nieterminalnych. *Lista_modułów_wyliczających* definiuje "treści modułu wyliczającego." *Lista_modułów_wyliczających* jest szczegółowo opisana poniżej.

Jeśli deklaracja znacznika jest widoczny, kolejne deklaracje, które Użyj tagu, ale pominięcie *lista_modułów_wyliczających* Określ poprzednio zadeklarowany Typ wyliczany. Znacznik musi odwoływać się do zdefiniowanego typu wyliczenia, a ten typ wyliczenia musi być w bieżącym zakresie. Ponieważ typ wyliczeniowy jest zdefiniowany w innym miejscu, *lista_modułów_wyliczających* nie jest widoczna w tej deklaracji. Deklaracje typów pochodnych wyliczeń i `typedef` deklaracje dla typów wyliczeń można użyć tagu wyliczenie, przed zdefiniowaniem typ wyliczenia.

## <a name="syntax"></a>Składnia

*Moduł wyliczający listę*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Moduł wyliczający*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Moduł wyliczający listę* **,** *modułu wyliczającego*

*Moduł wyliczający*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Stała wyliczenia* **=** *wyrażenia stałego*

*Stała wyliczenia*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*

Każdy *stała wyliczenia* w *listy wyliczenia* nazwy wartości wyliczenia zestawu. Domyślnie pierwszy *stała wyliczenia* jest skojarzony z wartością 0. Następne *stała wyliczenia* na liście jest skojarzony z wartością ( *wyrażenie_stałe* + 1), chyba że jawnie skojarzyć z inną wartością. Nazwa *stała wyliczenia* jest równoważne z jej wartość.

Możesz użyć *stała wyliczenia = wyrażenie stałe* zastąpić domyślną kolejność wartości. W związku z tym jeśli *stała wyliczenia = wyrażenie stałe* pojawia się w *lista_modułów_wyliczających*, *stała wyliczenia* jest skojarzona z wartości podanej przez *wyrażenie_stałe*. *Wyrażenie_stałe* musi mieć `int` wpisz i może być ujemna.

Następujące reguły stosuje się do elementów członkowskich wyliczenia zestawu:

- Wyliczenia mogą zawierać zduplikowanych wartości stałych. Na przykład można skojarzyć wartość 0 z dwóch różnych identyfikatorów, być może o nazwie `null` i `zero`, w tym samym zestawie.

- Identyfikatory na liście wyliczenia musi się różnić od innych identyfikatorów w tym samym zakresie z taką samą widoczność, w tym zwykłej nazwy zmiennych i identyfikatory w inne listy wyliczenia.

- Tagi wyliczania przestrzegają normalne reguły określania zakresów. Muszą być różne od innych wyliczenie, struktury i złożenia tagi z tej samej widoczności.

## <a name="examples"></a>Przykłady

Te przykłady ilustrują deklaracje modułów wyliczających:

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

Wartość 0 jest skojarzony z `saturday` domyślnie. Identyfikator `sunday` jest jawnie ustawiona na 0. Domyślnie pozostałych identyfikatorów są nadawane wartości od 1 do 5.

W tym przykładzie wartość z zakresu od zestawu `DAY` jest przypisany do zmiennej `today`.

```
enum DAY today = wednesday;
```

Należy pamiętać, że nazwa stałej wyliczenia jest używana do przypisywania wartości. Ponieważ `DAY` typ wyliczeniowy został wcześniej zadeklarowany, tylko tag wyliczenie `DAY` jest konieczne.

Aby jawnie przypisać wartość do zmiennej typu wyliczeniowego danych, należy użyć rzutowania typu:

```
workday = ( enum DAY ) ( day_value - 1 );
```

To rzutowanie jest zalecana w języku C, ale nie jest wymagane.

```
enum BOOLEAN  /* Declares an enumeration data type called BOOLEAN */
{
    false,     /* false = 0, true = 1 */
    true
};

enum BOOLEAN end_flag, match_flag; /* Two variables of type BOOLEAN */
```

Ta deklaracja może zostać określony jako

```
enum BOOLEAN { false, true } end_flag, match_flag;\
```

lub jako

```
enum BOOLEAN { false, true } end_flag;
enum BOOLEAN match_flag;
```

Przykład, który używa tych zmiennych może wyglądać następująco:

```
if ( match_flag == false )
    {
     .
     .   /* statement */
     .
    }
    end_flag = true;
```

Moduł wyliczający nienazwane typy danych mogą być także zadeklarowane. Nazwa typu danych zostanie pominięty, ale mogą być deklarowane zmienne. Zmienna `response` jest zmienną typu zdefiniowanego:

```
enum { yes, no } response;
```

## <a name="see-also"></a>Zobacz też

[Wyliczenia](../cpp/enumerations-cpp.md)