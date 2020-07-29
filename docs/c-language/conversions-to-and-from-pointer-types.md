---
title: Konwersje do i z typów wskaźnika
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 6358216e72f054becf33d18aadb6a3a51bab8363
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218900"
---
# <a name="conversions-to-and-from-pointer-types"></a>Konwersje do i z typów wskaźnika

Wskaźnik do jednego typu wartości może być przekonwertowany na wskaźnik do innego typu. Jednakże wynik może być niezdefiniowany, ze względu na wymagania wyrównania i rozmiary różnych typów w magazynie. Wskaźnik do obiektu może być przekonwertowany na wskaźnik do obiektu, którego typ wymaga mniejszego lub takiego samego wyrównania w magazynie i na odwrót bez zmiany.

Wskaźnik do **`void`** można przekonwertować na wskaźnik do dowolnego typu, bez ograniczeń lub utraty informacji. Jeśli wynik jest konwertowany z powrotem na oryginalny typ, oryginalny wskaźnik jest odzyskiwany.

Jeżeli wskaźnik jest konwertowany na inny wskaźnik tego samego typu, ale o różnych lub dodatkowych kwalifikatorach, nowy wskaźnik jest taki sam jak stary, z wyjątkiem ograniczeń nałożonych przez nowy kwalifikator.

Wartość wskaźnika można też przekonwertować na wartość całkowitą. Ścieżka konwersji zależy od rozmiaru wskaźnika i rozmiaru typu całkowitego, zgodnie z następującymi zasadami:

- Jeśli rozmiar wskaźnika jest większy niż lub równy rozmiarowi typu całkowitego, wskaźnik przy konwersji zachowuje się jak wartość nieoznaczona, z tym wyjątkiem, że nie można go przekonwertować na wartość zmiennoprzecinkową.

- Jeśli wskaźnik jest mniejszy niż typ całkowity, wskaźnik jest najpierw konwertowany na wskaźnik o tym samym rozmiarze co typ całkowity, a następnie konwertowany na typ całkowity.

I odwrotnie typ całkowity może być konwertowany na typ wskaźnika, zgodnie z następującymi zasadami:

- Jeśli typ całkowity ma taki sam rozmiar jak typ wskaźnika, konwersja powoduje po prostu traktowanie wartości całkowitej jako wskaźnika (liczba całkowita nieoznaczona).

- Jeśli rozmiar typu całkowitego różni się od rozmiaru typu wskaźnika, typ całkowity jest najpierw konwertowany na rozmiar wskaźnika, przy użyciu ścieżek konwersji podanych w [konwersji tabel z podpisanych typów całkowitych](../c-language/conversions-from-signed-integral-types.md) i [konwersji z niepodpisanych typów całkowitych](../c-language/conversions-from-unsigned-integral-types.md). Następnie jest ona traktowana jako wartość wskaźnika.

Całkowite wyrażenie stałe z wartością 0 lub takie rzutowanie wyrażenia na typ **`void`** <strong>\*</strong> może być konwertowane przez rzutowanie typu, przez przypisanie lub przez porównanie do wskaźnika dowolnego typu. Daje to pusty wskaźnik równy innemu pustemu wskaźnikowi tego samego typu, ale taki pusty wskaźnik nie jest równy żadnemu innemu wskaźnikowi do funkcji lub obiektu. Wartości całkowite inne niż stała 0 można przekonwertować na typ wskaźnika, ale wynik nie jest przenośny.

## <a name="see-also"></a>Zobacz także

[Konwersje przypisań](../c-language/assignment-conversions.md)
