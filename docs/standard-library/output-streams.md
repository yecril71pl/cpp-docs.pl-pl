---
title: Strumienie wyjściowe
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: e650f9fd0bbc7ad483363706e632686e8ec3749e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450174"
---
# <a name="output-streams"></a>Strumienie wyjściowe

Obiekt strumienia wyjściowego jest miejscem docelowym dla bajtów. Trzy najważniejsze klasy strumienia wyjściowego to `ostream`, `ofstream`, i `ostringstream`.

Klasa, za pomocą klasy `basic_ostream`pochodnej, obsługuje wstępnie zdefiniowane obiekty strumienia: `ostream`

- `cout`Wyjście standardowe

- `cerr`błąd standardowy z ograniczoną buforowaniem

- `clog``cerr` podobnie jak w przypadku pełnego buforowania

Obiekty są rzadko skonstruowane `ostream`; często używane są wstępnie zdefiniowane obiekty. W niektórych przypadkach można ponownie przypisać wstępnie zdefiniowane obiekty po uruchomieniu programu. `ostream` Klasa, którą można skonfigurować dla operacji buforowanej lub niebuforowanej, najlepiej nadaje się do sekwencyjnego wyjścia w trybie tekstowym. Wszystkie funkcje klasy podstawowej, `ios`,, są zawarte w. `ostream` W przypadku konstruowania obiektu klasy `ostream`należy `streambuf` określić obiekt dla konstruktora.

`ofstream` Klasa obsługuje dane wyjściowe pliku dyskowego. Jeśli potrzebujesz dysku wyjściowego, Utwórz obiekt klasy `ofstream`. Można określić, czy `ofstream` obiekty będą akceptować dane binarne lub w trybie tekstowym podczas konstruowania `ofstream` `open` obiektu, czy podczas wywoływania funkcji składowej obiektu. Wiele opcji formatowania i funkcji elementów członkowskich stosuje `ofstream` się do obiektów, a wszystkie funkcje klas `ios` podstawowych i `ostream` są uwzględniane.

Jeśli określisz nazwę pliku w konstruktorze, ten plik zostanie automatycznie otwarty podczas konstruowania obiektu. W przeciwnym razie można użyć `open` funkcji elementu członkowskiego po wywołaniu domyślnego konstruktora.

Podobnie jak w przypadku funkcji `sprintf_s` `ostringstream` Run-Time Klasa obsługuje dane wyjściowe do ciągów w pamięci. Aby utworzyć ciąg w pamięci przy użyciu formatowania strumienia we/wy, Skonstruuj obiekt klasy `ostringstream`.

## <a name="in-this-section"></a>W tej sekcji

[Konstruowanie obiektów strumienia wyjściowego](../standard-library/constructing-output-stream-objects.md)

[Korzystanie z operatorów wstawiania i formatu kontrolującego](../standard-library/using-insertion-operators-and-controlling-format.md)

[Funkcje składowe strumienia pliku danych wyjściowych](../standard-library/output-file-stream-member-functions.md)

[Efekty buforowania](../standard-library/effects-of-buffering.md)

[Wyjściowe pliki binarne](../standard-library/binary-output-files.md)

[Przeciążanie operatora << dla własnych klas](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[Tworzenie manipulatorów bez argumentów](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>Zobacz także

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream](../standard-library/basic-ostringstream-class.md)\
[iostream, programowanie](../standard-library/iostream-programming.md)
