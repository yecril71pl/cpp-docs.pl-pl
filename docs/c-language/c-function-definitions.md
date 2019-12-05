---
title: Definicje funkcji języka C
ms.date: 11/04/2016
helpviewer_keywords:
- function declarators
- function definitions
- declaring functions, about function declarations
- declaring functions, declarators
- functions [C], parameters
- declarators, functions
- function parameters, function definitions
- function body
- declaring functions, variables
ms.assetid: ebab23c8-6eb8-46f3-b21d-570cd8457a80
ms.openlocfilehash: 5cf56375df417ac68b3e03d00f2bd7770ee571e8
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857141"
---
# <a name="c-function-definitions"></a>Definicje funkcji języka C

Definicja funkcji określa nazwę funkcji, typy i liczbę parametrów, które oczekuje na odebranie, i typ zwracany. Definicja funkcji zawiera również treść funkcji z deklaracjami zmiennych lokalnych i instrukcji, które określają działanie funkcji.

## <a name="syntax"></a>Składnia

*Jednostka translation*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracja zewnętrzna* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;— *deklaracja zewnętrzna* *jednostki tłumaczenia*

*deklaracja zewnętrzna*:/\* dozwolone tylko w zewnętrznym zakresie (pliku) \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*funkcji — definicja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*

*definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarator, *specyfikatory deklaracji*<sub>opt</sub> *-SEQ*<sub>opt</sub> *deklaracji-list*<sub>opt</sub> *złożonej-instrukcja*

atrybut \* / *-SEQ* jest \*em specyficznym dla firmy Microsoft /

Parametry prototypu:

*specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *specyfikatora klasy magazynu* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *specyfikatora typu*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<sub></sub> *kwalifikatora typu*

*Deklaracja-lista*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklaracji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja list*

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;deklarator *wskaźnika*"<sub>opt</sub> *Direct-"*

*Direct-deklarator*:/\* deklarator funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy parametrów typu* **)**  / \* deklaratora nowy styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio* **(** *listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**  / \* Obsolete stylu deklarator \*/

Lista parametrów w definicji używa następującej składni:

*Typ parametru-list*:/\* listy parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parameter-declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parametrów-list* **,** *deklaracji parametru*

*Deklaracja parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*specyfikatory deklaracji* *deklarator*<br/>
&nbsp;&nbsp;&nbsp;*specyfikatora deklaracji*<sub></sub> &nbsp;

Lista parametrów w definicji funkcji starego stylu używa następującej składni:

*identyfikatory-list*:/\* używane w definicjach i deklaracjach funkcji przestarzałego stylu \*/<br/>
&nbsp;&nbsp;&nbsp;*identyfikator* &nbsp;<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista identyfikatorów* **,** *identyfikator*

Składnia dla treści funkcji jest następująca:

*instrukcja złożona*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;instrukcji **{** *Deklaracja-list*<sub>opt</sub> *-list*<sub>opt</sub> **}**

Jedyne specyfikatory klasy magazynu, które mogą modyfikować deklarację funkcji, są **extern** i **statyczne**. Specyfikator **extern** oznacza, że funkcja może być przywoływana z innych plików; oznacza to, że nazwa funkcji jest eksportowana do konsolidatora. Specyfikator **statyczny** oznacza, że funkcji nie można odwoływać się od innych plików; oznacza to, że nazwa nie jest eksportowana przez konsolidator. Jeśli Klasa magazynu nie jest wyświetlana w definicji funkcji, założono **extern** . W każdym przypadku funkcja jest zawsze widoczna z punktu definicji do końca pliku.

Opcjonalne *specyfikatory deklaracji* i obowiązkowe *deklarator* razem określają typ zwracany i nazwę funkcji. *Deklarator* to kombinacja identyfikatorów, która nazywa funkcję i nawiasy po nazwie funkcji. Opcjonalny *atrybut-seq* nieterminalu jest funkcją specyficzną dla firmy Microsoft zdefiniowaną w [atrybutach funkcji](../c-language/function-attributes.md).

*Direct-deklarator* (w składni *deklarator* ) określa nazwę zdefiniowanej funkcji i identyfikatory jej parametrów. Jeśli polecenie *Direct-deklarator* zawiera *listę typów parametrów*, lista określa typy wszystkich parametrów. Takie deklarator również służy jako prototyp funkcji dla późniejszego wywołania funkcji.

*Deklaracja* na *liście deklaracji* w definicjach funkcji nie może zawierać *specyfikatora klasy magazynu* innego niż **register**. *Specyfikator typu* w składni *specyfikatorów deklaracji* można pominąć tylko wtedy, gdy Klasa magazynu **rejestru** jest określona dla wartości typu **int** .

*Instrukcja złożona* jest treścią funkcji zawierającą deklaracje zmiennej lokalnej, odwołania do elementów zadeklarowanych zewnętrznie i instrukcji.

Sekcje [atrybutów funkcji](../c-language/function-attributes.md), [klasy magazynu](../c-language/storage-class.md), [typu zwracanego](../c-language/return-type.md), [parametrów](../c-language/parameters.md)i [treści funkcji](../c-language/function-body.md) opisują składniki definicji funkcji szczegółowo.

## <a name="see-also"></a>Zobacz także

[Funkcje](../c-language/functions-c.md)
