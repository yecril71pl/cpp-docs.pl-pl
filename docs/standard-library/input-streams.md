---
title: Strumienie wejściowe
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 5dc3fa0af76f73897fe1181d944eb34c8d05bc64
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449329"
---
# <a name="input-streams"></a>Strumienie wejściowe

Obiekt strumienia danych wejściowych jest źródłem bajtów. Trzy najważniejsze klasy strumienia wejściowego to [IStream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md)i [istringstream —](../standard-library/basic-istringstream-class.md).

`istream` Klasa jest Najlepsza do użycia w sekwencyjnym wejściu w trybie tekstowym. Można skonfigurować obiekty klasy `istream` dla operacji buforowanej lub niebuforowanej. Wszystkie funkcje klasy podstawowej, `ios`,, są zawarte w. `istream` Obiekty z klasy `istream`są rzadko konstruowane. Zamiast tego zwykle używany jest wstępnie zdefiniowany `cin` obiekt, który jest obiektem klasy [ostream](../standard-library/basic-ostream-class.md). W niektórych przypadkach można przypisać `cin` do innych obiektów strumienia po uruchomieniu programu.

`ifstream` Klasa obsługuje dane wejściowe pliku dyskowego. Jeśli potrzebujesz pliku dyskowego tylko do wprowadzania danych, Utwórz obiekt klasy `ifstream`. Można określić dane binarne lub w trybie tekstowym. Jeśli określisz nazwę pliku w konstruktorze, plik zostanie automatycznie otwarty podczas konstruowania obiektu. W przeciwnym razie można użyć `open` funkcji po wywołaniu konstruktora domyślnego. Wiele opcji formatowania i funkcji Członkowskich ma zastosowanie `ifstream` do obiektów. Wszystkie funkcje klas `ios` podstawowych i `istream` są zawarte w `ifstream`.

Podobnie jak w przypadku `sscanf_s`funkcji biblioteki `istringstream` , Klasa obsługuje dane wejściowe z ciągów w pamięci. Aby wyodrębnić dane z tablicy znaków, która ma terminator o wartości null, przydzielić i zainicjować ciąg, a następnie utworzyć obiekt klasy `istringstream`.

## <a name="in-this-section"></a>W tej sekcji

[Konstruowanie obiektów strumienia danych wejściowych](../standard-library/constructing-input-stream-objects.md)

[Korzystanie z operatorów wyodrębniania](../standard-library/using-extraction-operators.md)

[Testowanie pod kątem wyodrębniania błędów](../standard-library/testing-for-extraction-errors.md)

[Manipulatory strumieni wejścia](../standard-library/input-stream-manipulators.md)

[Funkcje składowe strumienia wejściowego](../standard-library/input-stream-member-functions.md)

[Przeciążanie operatora >> dla własnych klas](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>Zobacz także

[iostream, programowanie](../standard-library/iostream-programming.md)
