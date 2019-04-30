---
title: Strumienie wejściowe
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 0f56f5ffc8e61c0881eddbbd65e1c431b9219674
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404926"
---
# <a name="input-streams"></a>Strumienie wejściowe

Obiekt strumienia wejściowego jest źródłem bajtów. Są trzy najważniejsze klasy strumień wejściowy [istream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md), i [istringstream](../standard-library/basic-istringstream-class.md).

`istream` Klasy najlepiej nadaje się do trybu sekwencyjnego tekstu w danych wejściowych. Można skonfigurować obiektów klasy `istream` buforowane lub Niebuforowane operacji. Wszystkie funkcje klasy bazowej, `ios`, znajduje się w `istream`. Konstruujesz rzadko obiektów z klasy `istream`. Zamiast tego zazwyczaj użyje wstępnie zdefiniowanego `cin` obiektu, który jest faktycznie obiekt klasy [ostream](../standard-library/basic-ostream-class.md). W niektórych przypadkach można przypisać `cin` do innych obiektów strumień po uruchomieniu programu.

`ifstream` Klasa obsługuje dysku pliku wejściowego. Jeśli potrzebujesz tylko szyfrowanie plików na dysku, utworzyć obiekt klasy `ifstream`. Można określić dane binarne lub tekstowej. Jeśli określisz parametr filename w konstruktorze, plik jest automatycznie otwierany, gdy obiekt jest konstruowany. W przeciwnym razie można użyć `open` funkcji po wywołaniu konstruktora domyślnego. Wiele funkcji formatowania opcje i elementów członkowskich dotyczą `ifstream` obiektów. Wszystkie funkcje klasy bazowe `ios` i `istream` znajduje się w `ifstream`.

Funkcja biblioteki, takie jak `sscanf_s`, `istringstream` klasa obsługuje dane wejściowe z ciągów w pamięci. Aby wyodrębnić dane z tablicy znaków, który ma terminator o wartości null, przydzielanie i inicjuje ciąg, a następnie utworzyć obiekt klasy `istringstream`.

## <a name="in-this-section"></a>W tej sekcji

[Konstruowanie obiektów strumienia danych wejściowych](../standard-library/constructing-input-stream-objects.md)

[Korzystanie z operatorów wyodrębniania](../standard-library/using-extraction-operators.md)

[Testowanie pod kątem wyodrębniania błędów](../standard-library/testing-for-extraction-errors.md)

[Manipulatory strumieni wejścia](../standard-library/input-stream-manipulators.md)

[Funkcje składowe strumienia wejściowego](../standard-library/input-stream-member-functions.md)

[Przeciążanie operatora >> dla własnych klas](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>Zobacz także

[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
