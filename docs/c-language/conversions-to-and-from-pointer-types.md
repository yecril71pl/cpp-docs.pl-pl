---
title: Konwersje do i z typów wskaźnika
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 2d907dbcf4f826d364fb68ce65f7d44c6cfe97cd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147246"
---
# <a name="conversions-to-and-from-pointer-types"></a>Konwersje do i z typów wskaźnika

Wskaźnik do jednego typu wartości może być przekonwertowany na wskaźnik do innego typu. Jednakże wynik może być niezdefiniowany, ze względu na wymagania wyrównania i rozmiary różnych typów w magazynie. Wskaźnik do obiektu może być przekonwertowany na wskaźnik do obiektu, którego typ wymaga mniejszego lub takiego samego wyrównania w magazynie i na odwrót bez zmiany.

Wskaźnik do `void` może być przekonwertowany na lub ze wskaźnika do dowolnego typu, bez ograniczeń lub utraty informacji. Jeśli wynik jest konwertowany z powrotem na oryginalny typ, oryginalny wskaźnik jest odzyskiwany.

Jeżeli wskaźnik jest konwertowany na inny wskaźnik tego samego typu, ale o różnych lub dodatkowych kwalifikatorach, nowy wskaźnik jest taki sam jak stary, z wyjątkiem ograniczeń nałożonych przez nowy kwalifikator.

Wartość wskaźnika można też przekonwertować na wartość całkowitą. Ścieżka konwersji zależy od rozmiaru wskaźnika i rozmiaru typu całkowitego, zgodnie z następującymi zasadami:

- Jeśli rozmiar wskaźnika jest większy niż lub równy rozmiarowi typu całkowitego, wskaźnik przy konwersji zachowuje się jak wartość nieoznaczona, z tym wyjątkiem, że nie można go przekonwertować na wartość zmiennoprzecinkową.

- Jeśli wskaźnik jest mniejszy niż typ całkowity, wskaźnik jest najpierw konwertowany na wskaźnik o tym samym rozmiarze co typ całkowity, a następnie konwertowany na typ całkowity.

I odwrotnie typ całkowity może być konwertowany na typ wskaźnika, zgodnie z następującymi zasadami:

- Jeśli typ całkowity ma taki sam rozmiar jak typ wskaźnika, konwersja powoduje po prostu traktowanie wartości całkowitej jako wskaźnika (liczba całkowita nieoznaczona).

- Jeśli rozmiar typu całkowitego jest różny od rozmiaru typu wskaźnika, typ całkowity jest najpierw konwertowany na rozmiar wskaźnika, używając ścieżek konwersji podanych w tabelach [konwersja z typów całkowitych oznaczonych](../c-language/conversions-from-signed-integral-types.md) i [ Konwersja z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md). Następnie jest ona traktowana jako wartość wskaźnika.

Wyrażenie stałej całkowitej o wartości 0 lub Rzutowanie na typ wyrażenia **void** <strong>\*</strong> mogą być konwertowane przez rzutowanie typu, przez przypisanie lub w porównaniu do wskaźnika dowolnego typu. Daje to pusty wskaźnik równy innemu pustemu wskaźnikowi tego samego typu, ale taki pusty wskaźnik nie jest równy żadnemu innemu wskaźnikowi do funkcji lub obiektu. Wartości całkowite inne niż stała 0 można przekonwertować na typ wskaźnika, ale wynik nie jest przenośny.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
