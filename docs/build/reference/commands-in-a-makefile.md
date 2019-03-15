---
title: Polecenia w pliku reguł programu Make
ms.date: 11/04/2016
helpviewer_keywords:
- commands, makefiles
ms.assetid: 8085517e-42f4-493b-b8f8-44311fc08c64
ms.openlocfilehash: fcb8737070931cf95d7bfb3971a84e22c7ad70a4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823250"
---
# <a name="commands-in-a-makefile"></a>Polecenia w pliku reguł programu Make

Opis reguły blokowanie lub wnioskowania określa blok polecenia do uruchomienia, jeśli zależność jest nieaktualna. NMAKE Wyświetla każde polecenie przed uruchomieniem go, chyba że /S, **. DYSKRETNEJ**, **! CMDSWITCHES**, lub \@ jest używany. NMAKE szuka reguły wnioskowania dopasowania, jeśli blok opis nie następuje w bloku poleceń.

Blok poleceń zawiera co najmniej jedno polecenie, każdą w osobnym wierszu. Nie pusty wiersz, mogą występować między zależność lub reguły i blok poleceń. Jednakże wiersz zawierający tylko spacje lub tabulatory mogą być wyświetlane; Ten wiersz jest interpretowane jako polecenie o wartości null i nie występują błędy. Puste wiersze są dozwolone między wiersze polecenia.

Wiersz polecenia rozpoczyna się od spacji lub karty. Ukośnik odwrotny (\), w którym następuje znak nowego wiersza jest interpretowany jako miejsca w poleceniu; użyć znaku ukośnika na końcu wiersza, aby kontynuować do następnego wiersza polecenia. NMAKE interpretuje ukośnik odwrotny dosłownie Jeśli jakikolwiek inny znak, w tym spacji lub tabulatorów, następuje po odwrotnym ukośniku.

Polecenie poprzedzone średnika (;) mogą być wyświetlane na reguły linii lub wnioskowania zależności, czy następuje po bloku poleceń:

```
project.obj : project.c project.h ; cl /c project.c
```

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?

[Modyfikatory poleceń](command-modifiers.md)

[Składnia nazwy pliku części](filename-parts-syntax.md)

[Pliki wbudowane w pliku reguł programu make](inline-files-in-a-makefile.md)

## <a name="see-also"></a>Zobacz także

[NMAKE — dokumentacja](nmake-reference.md)
