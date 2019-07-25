---
title: Manipulatory strumieni wejścia
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: d9a6f00f1b5a52d4d388ace376676b45547bdd49
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451029"
---
# <a name="input-stream-manipulators"></a>Manipulatory strumieni wejścia

Wiele manipulowania, takich jak [setprecision](../standard-library/iomanip-functions.md#setprecision), jest zdefiniowanych dla `ios` klasy i w związku z tym ma zastosowanie do strumieni wejściowych. Niektóre manipulowania, jednak faktycznie mają wpływ na obiekty strumienia wejściowego. Dla tych, które to najważniejsze, są podstawy manipulowania, `dec`, `oct`, i `hex`, które określają bazę konwersji używaną z liczbami ze strumienia wejściowego.

Przy wyodrębnianiu `hex` Manipulator umożliwia przetwarzanie różnych formatów wejściowych. Na przykład, c, C, 0xC, 0xC, 0Xc i 0XC są interpretowane jako dziesiętna liczba całkowita 12. Dowolny znak inny niż od 0 do 9, od A do F, a do f, x, i X kończy konwersję liczbową. W związku z `"124n5"` tym sekwencja jest konwertowana na liczbę 124 z ustawionym bitem [basic_ios:: Fail](../standard-library/basic-ios-class.md#fail) .

## <a name="see-also"></a>Zobacz także

[Strumienie wejściowe](../standard-library/input-streams.md)
