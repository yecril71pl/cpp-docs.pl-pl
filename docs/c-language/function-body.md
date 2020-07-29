---
title: Treść funkcji
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
ms.openlocfilehash: 2ae73ab4ca91e06e3b6cd41166a8d05ae0857e4a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229704"
---
# <a name="function-body"></a>Treść funkcji

*Treść funkcji* jest złożonym wyrażeniem zawierającym instrukcje określające działanie funkcji.

## <a name="syntax"></a>Składnia

*definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Deklaracja-specyfikators*<sub>opt</sub> *Attribute-SEQ*<sub>opt</sub> *deklarator* *deklaracji-list*<sub>opt</sub> *złożone-instrukcja*

/\**atrybut-seq* jest specyficzny dla firmy Microsoft\*/

*instrukcja złożona*:/ \* treść funkcji\*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *deklaracji*<sub>opt</sub> *instrukcji SELECT-list*<sub>opt</sub> **}**

Zmienne zadeklarowane w treści funkcji, znane jako *zmienne lokalne*, mają **`auto`** klasę magazynu, chyba że określono inaczej. Po wywołaniu funkcji magazyn jest tworzony dla zmiennych lokalnych i są wykonywane lokalne inicjalizacje. Kontrola wykonywania przechodzi do pierwszej instrukcji w *instrukcji złożonej* i kontynuuje do momentu **`return`** wykonania instrukcji lub napotkania końca treści funkcji. Następnie formant wraca do punktu, w którym wywołano funkcję.

**`return`** Instrukcja zawierająca wyrażenie musi być wykonana, jeśli funkcja ma zwracać wartość. Wartość zwracana funkcji jest niezdefiniowana, jeśli instrukcja nie **`return`** jest wykonywana lub **`return`** instrukcja nie zawiera wyrażenia.

## <a name="see-also"></a>Zobacz także

[Definicje funkcji języka C](../c-language/c-function-definitions.md)
