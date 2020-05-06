---
title: Odejmowanie (-)
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
ms.openlocfilehash: 5c9510cf3708ef049b5dac213fa3de894fcd4a07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157763"
---
# <a name="subtraction--"></a>Odejmowanie (-)

Operator odejmowania (**-**) Odejmuje drugi operand od pierwszego. Oba operandy mogą być typu całkowitego lub zmiennoprzecinkowego lub jeden operand może być wskaźnikiem, a drugą liczbą całkowitą.

Gdy są odejmowane dwa wskaźniki, różnica jest konwertowana na podpisaną wartość całkowitą przez podzielenie różnicy przez rozmiar wartości typu, którego dotyczy wskaźnik. Rozmiar wartości całkowitej jest definiowany przez typ **ptrdiff_t** w standardowym pliku STDDEF. C. Wynik przedstawia liczbę pozycji pamięci tego typu między dwoma adresami. Wynik jest gwarantowany tylko dla dwóch elementów tej samej tablicy, zgodnie z opisem w obszarze [arytmetyczny wskaźnik](../c-language/pointer-arithmetic.md).

W przypadku odejmowania wartości całkowitej od wartości wskaźnika operator odejmowania konwertuje wartość całkowitą (*i*) przez pomnożenie jej przez rozmiar wartości, która jest adresem wskaźnika. Po konwersji wartość *całkowita reprezentuje położenie* pamięci, gdzie każda pozycja ma długość określoną przez typ wskaźnika. Gdy przekonwertowana wartość całkowita zostanie odjęta od wartości wskaźnika, wynikiem jest adres pamięci, *po* którym naliczane są adresy przed pierwotnym adresem. Nowy wskaźnik wskazuje wartość typu rozkierowanego przez oryginalną wartość wskaźnika.

## <a name="see-also"></a>Zobacz też

[Operatory dodawania języka C](../c-language/c-additive-operators.md)
