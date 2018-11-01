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
ms.openlocfilehash: dd396cb182aeae9ef587ab58f04893cf0283a8a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507214"
---
# <a name="c-function-definitions"></a>Definicje funkcji języka C

Definicja funkcji Określa nazwę funkcji, typy i liczbę parametrów, które oczekuje, aby otrzymać i jego typem zwracanym. Definicja funkcji obejmuje również treści funkcji za pomocą deklaracji jego zmienne lokalne i instrukcje, które określają, jak działa funkcja.

## <a name="syntax"></a>Składnia

*jednostki translacji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja zewnętrzne* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*jednostki translacji* *deklaracji zewnętrzne*

*Deklaracja zewnętrzne*: /\* dozwolone tylko w zakresie zewnętrzne (plik) \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Definicja funkcji*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*

*Definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> *atrybutu seq*<sub>zoptymalizowany pod kątem</sub> *deklaratora* *lista deklaracji*  <sub>zoptymalizowany pod kątem</sub> *compound-statement*

/\* *Atrybut seq* jest Specific dla Microsoft \*/

Prototyp parametry są następujące:

*Specyfikatory deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Storage-class-specifier* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Kwalifikator typu* *specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub>

*Lista deklaracji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista deklaracji* *deklaracji*

*deklarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*wskaźnik*<sub>zoptymalizowany pod kątem</sub> *deklaratora bezpośrednie*

*deklarator bezpośrednio*: /\* deklaratora funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio***(***listy parametrów typu***)**  / \* deklaratora nowy styl \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*deklarator bezpośrednio***(***listy identyfikatorów*<sub>zoptymalizowany pod kątem</sub> **)**  / \* Obsolete stylu deklarator \*/

Lista parametrów w definicji używa następującej składni:

*listy parametrów typu*: /\* listy parametrów \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,...**

*Lista parametrów*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja parametru*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista parametrów* **,***deklaracji parametru*

*Deklaracja parametru*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *deklaratora*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji* *abstrakcyjny declarator*<sub>zoptymalizowany pod kątem</sub>

Lista parametrów w definicji funkcji w starym stylu używa następującej składni:

*Lista identyfikatorów*: /\* używany w funkcji przestarzały styl definicje i deklaracje \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Identyfikator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Lista identyfikatorów* **,***identyfikator*

Składnia dla treści funkcji jest następująca:

*Compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *lista deklaracji*<sub>zoptymalizowany pod kątem</sub> *listy instrukcji*<sub>zoptymalizowany pod kątem</sub> **}**

Są tylko specyfikatory klasy magazynowania, które można modyfikować deklaracji funkcji **extern** i **statyczne**. **Extern** specyfikator oznacza, że funkcja mogą być przywoływane z innych plików; oznacza to, że nazwa funkcji jest eksportowana do konsolidatora. **Statyczne** specyfikator oznacza, że funkcja nie może być przywoływany z innych plików; oznacza to, że nazwa nie jest eksportowane przez konsolidator. Jeśli żadna z klas magazynu znajduje się w definicji funkcji **extern** zakłada, że. W każdym przypadku funkcja zawsze jest widoczny w punkcie definicji do końca pliku.

Opcjonalny *specyfikatory deklaracji* i jest to obowiązkowe *deklaratora* wspólnie określić typ zwracany przez funkcję i nazwę. *Deklaratora* jest kombinacją identyfikator, który nazwy funkcji i nawiasów po nazwie funkcji. Opcjonalny *atrybutu seq* nonterminal jest specyficzne dla firmy Microsoft funkcji zdefiniowanych w [atrybuty funkcji](../c-language/function-attributes.md).

*Bezpośrednio declarator* (w *deklaratora* składni) Określa nazwę funkcji definiowanego i identyfikatory jego parametrów. Jeśli *bezpośrednio declarator* obejmuje *listy parametrów typu*, listy określa typy wszystkich parametrów. Takie deklaratora służy również jako prototyp funkcji nowsze wywołań funkcji.

A *deklaracji* w *lista deklaracji* w funkcji nie może zawierać definicje *storage-class-specifier* innych niż **zarejestrować**. *Specyfikator typu* w *specyfikatory deklaracji* składni można pominąć, tylko wtedy, gdy **zarejestrować** klasę magazynu jest określona dla wartości **int** typu.

*Compound-statement* stanowi treści funkcji, zawierająca deklaracje zmiennych lokalnych, odwołania do elementów zewnętrznie zadeklarowana i instrukcji.

Sekcje [atrybuty funkcji](../c-language/function-attributes.md), [klasę magazynu](../c-language/storage-class.md), [typie zwracanym](../c-language/return-type.md), [parametry](../c-language/parameters.md), i [treści funkcji](../c-language/function-body.md) składników definicji funkcji szczegółowo opisano.

## <a name="see-also"></a>Zobacz też

[Funkcje](../c-language/functions-c.md)