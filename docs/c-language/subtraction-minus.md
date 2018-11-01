---
title: Odejmowania (-)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 369096025a67c67775584928d1ee3264a5a10d94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480057"
---
# <a name="subtraction--"></a>Odejmowania (-)

Operator odejmowania (**-**) odejmuje drugiego operandu od pierwszego. Oba operandy może być typu całkowitego lub zmiennoprzecinkowego typy, lub jeden argument może być wskaźnika, a drugi liczbą całkowitą.

Gdy dwa wskaźniki są odejmowane, różnica jest konwertowana na wartość całkowitą ze znakiem przez podzielenie otrzymanej różnicy przez rozmiar wartość typu, adres wskaźników. Rozmiar wartość całkowitą jest definiowany przez typ **ptrdiff_t —** w standardowych dołączonych plików STDDEF. H. Wynik przedstawia liczbę pozycji pamięci tego typu między dwoma adresami. Wynik jest tylko gwarantowane jest zrozumiałe dla dwóch elementów w tej samej tablicy, zgodnie z opisem w [arytmetyki wskaźnika](../c-language/pointer-arithmetic.md).

Gdy wartość jest odejmowany od wartości wskaźnika, operator odejmowania konwertuje wartość całkowitą (*i*) mnożąc przez rozmiar wartości, odnoszący się do wskaźnika. Po konwersji na wartość całkowitą reprezentuje *i* pozycji pamięci, w którym każdej pozycji ma długość określona przez typ wskaźnika. Gdy wartość przekonwertowana liczba całkowita jest odejmowany od wartości wskaźnika, wynik jest adres pamięci *i* pozycji przed oryginalnego adresu. Nowy wskaźnik wskazuje na wartość typu opisany w oryginalnej wartości wskaźnika.

## <a name="see-also"></a>Zobacz też

[Operatory dodawania języka C](../c-language/c-additive-operators.md)