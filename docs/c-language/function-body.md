---
title: Funkcja treści | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C], syntax
- variables, function syntax
- function definitions, function body
- function body
ms.assetid: f7e74822-fac8-4dc8-8f3a-2b1611da4640
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d30cb5429ebee0738aa7b7aab367d79867e92047
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43757822"
---
# <a name="function-body"></a>Treść funkcji

A *funkcji treści* jest instrukcji złożonej zawierającej instrukcje, które określają, jak działa funkcja.

## <a name="syntax"></a>Składnia

*Definicja funkcji*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Specyfikatory deklaracji*<sub>zoptymalizowany pod kątem</sub> *atrybutu seq*<sub>zoptymalizowany pod kątem</sub> *deklaratora* *lista deklaracji*  <sub>zoptymalizowany pod kątem</sub> *compound-statement*

/\* *Atrybut seq* jest Specific dla Microsoft \*/

*Compound-statement*: /\* treści funkcji \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *lista deklaracji*<sub>zoptymalizowany pod kątem</sub> *listy instrukcji*<sub>zoptymalizowany pod kątem</sub> **}**

Zmienne zadeklarowane w treści funkcji, znane jako *zmienne lokalne*, mają **automatycznie** klasy magazynu, chyba że określono inaczej. Po wywołaniu funkcji magazynu jest tworzony dla zmiennych lokalnych i lokalne inicjalizacje są wykonywane. Kontrola wykonywania przechodzi do pierwszej instrukcji w *compound-statement* i jest kontynuowane do **zwracają** zostaje wykonana instrukcja lub zostanie osiągnięty koniec treści funkcji. Formant powraca do punktu, w którym funkcja została wywołana.

A **zwracają** instrukcji zawierającej wyrażenie musi zostać wykonana, jeśli funkcja znajduje się w celu zwrócenia wartości. Wartość zwracana przez funkcję jest niezdefiniowana, jeśli nie **zwracają** zostaje wykonana instrukcja lub jeśli **zwracają** instrukcji nie zawiera wyrażenia.

## <a name="see-also"></a>Zobacz też

[Definicje funkcji języka C](../c-language/c-function-definitions.md)