---
title: Treść funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 2d2e04572de91b161237d999bb95cfda26256c54
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857102"
---
# <a name="function-body"></a>Treść funkcji

*Treść funkcji* jest złożonym wyrażeniem zawierającym instrukcje określające działanie funkcji.

## <a name="syntax"></a>Składnia

*definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators*<sub>opt</sub> *Attribute-SEQ*<sub>opt</sub> *deklarator* *deklaracji-list*<sub>opt</sub> *złożone-instrukcja*

/\**atrybut-seq* jest specyficzny dla firmy Microsoft\*/

*instrukcja złożona*:/\* treść funkcji\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklaracji*<sub>opt</sub> *instrukcji SELECT-list*<sub>opt</sub> **}**

Zmienne zadeklarowane w treści funkcji, znane jako *zmienne lokalne* **, mają klasy** magazynu autostorage, chyba że określono inaczej. Po wywołaniu funkcji magazyn jest tworzony dla zmiennych lokalnych i są wykonywane lokalne inicjalizacje. Kontrola wykonywania przechodzi do pierwszej instrukcji w *instrukcji złożonej* i kontynuuje do momentu wykonania instrukcji **Return** lub napotkania końca treści funkcji. Następnie formant wraca do punktu, w którym wywołano funkcję.

Instrukcja **Return** zawierająca wyrażenie musi być wykonana, jeśli funkcja ma zwracać wartość. Wartość zwracana funkcji jest niezdefiniowana, jeśli instrukcja **Return** nie jest wykonywana lub instrukcja **Return** nie zawiera wyrażenia.

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
