---
title: Strumienie wyjściowe
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: c64c46acca405f948e8314fb23944682adf09c43
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511114"
---
# <a name="output-streams"></a>Strumienie wyjściowe

Obiekt strumienia wyjściowego jest miejsce docelowe dla bajtów. Są trzy najważniejsze klasy strumieni danych wyjściowych `ostream`, `ofstream`, i `ostringstream`.

`ostream` Klasy do klasy pochodnej `basic_ostream`, obsługuje obiekty strumienia wstępnie zdefiniowane:

- `cout` Standardowe dane wyjściowe

- `cerr` Standardowy błąd za pomocą ograniczone buforowania

- `clog` Podobnie jak `cerr` , ale za pomocą pełnego buforowania

Obiekty rzadko są konstruowane na podstawie `ostream`; wstępnie zdefiniowane obiekty są zazwyczaj używane. W niektórych przypadkach można ponownie przypisać wstępnie zdefiniowanych obiektów po uruchomieniu programu. `ostream` Klasy, które można skonfigurować dla operacji buforowane lub Niebuforowane najlepiej nadaje się do trybu sekwencyjnego tekstu w danych wyjściowych. Wszystkie funkcje klasy bazowej, `ios`, znajduje się w `ostream`. Można utworzyć obiekt klasy `ostream`, należy określić `streambuf` obiekt do konstruktora.

`ofstream` Klasa obsługuje dane wyjściowe pliku dysku. Dysk tylko do danych wyjściowych, należy utworzyć obiekt klasy `ofstream`. Można określić czy `ofstream` obiektów akceptować dane trybu tekst lub dane binarne, przy konstruowaniu `ofstream` obiektu lub podczas wywoływania `open` funkcja elementu członkowskiego obiektu. Wiele funkcji formatowania opcje i elementów członkowskich dotyczą `ofstream` obiekty i wszystkie funkcje klasy bazowe `ios` i `ostream` jest dołączony.

Jeśli określisz parametr filename w Konstruktorze ten plik jest automatycznie otwierany, gdy obiekt jest konstruowany. W przeciwnym razie można użyć `open` funkcja elementu członkowskiego po wywołaniu konstruktora domyślnego.

Jak funkcja środowiska wykonawczego `sprintf_s`, `ostringstream` klasa obsługuje dane wyjściowe do ciągów w pamięci. Aby utworzyć ciąg w pamięci, korzystając z operacji We/Wy strumienia formatowania, należy utworzyć obiekt klasy `ostringstream`.

## <a name="in-this-section"></a>W tej sekcji

[Konstruowanie obiektów strumienia wyjściowego](../standard-library/constructing-output-stream-objects.md)

[Korzystanie z operatorów wstawiania i formatu kontrolującego](../standard-library/using-insertion-operators-and-controlling-format.md)

[Funkcje składowe strumienia pliku danych wyjściowych](../standard-library/output-file-stream-member-functions.md)

[Efekty buforowania](../standard-library/effects-of-buffering.md)

[Wyjściowe pliki binarne](../standard-library/binary-output-files.md)

[Przeciążanie operatora << dla własnych klas](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[Tworzenie manipulatorów bez argumentów](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>Zobacz także

[ofstream](../standard-library/basic-ofstream-class.md)<br/>
[ostringstream](../standard-library/basic-ostringstream-class.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
