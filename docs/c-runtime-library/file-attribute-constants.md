---
title: Stałe atrybutów pliku
ms.date: 11/04/2016
f1_keywords:
- A_HIDDEN
- _A_NORMAL
- _A_SUBDIR
- _A_RDONLY
- A_NORMAL
- A_SUBDIR
- _A_SYSTEM
- c.constants.file
- _A_HIDDEN
- A_RDONLY
- _A_ARCH
- A_ARCH
helpviewer_keywords:
- constants [C++], file attributes
- file attribute constants [C++]
- _A_SYSTEM constant
- files [C++], file attribute constants
- _A_SUBDIR constant
- _A_ARCH constant
- _A_NORMAL constant
- _A_HIDDEN constant
- _A_RDONLY constant
ms.assetid: 8dc8ccb9-99f5-446b-876c-7ebecc2f764f
ms.openlocfilehash: 271459c33cdcc1110222871bdca06d3f04edb497
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62343800"
---
# <a name="file-attribute-constants"></a>Stałe atrybutów pliku

## <a name="syntax"></a>Składnia

```
#include <io.h>
```

## <a name="remarks"></a>Uwagi

Te stałe określić atrybuty bieżącego pliku lub katalogu określonym przez funkcję.

Atrybuty są reprezentowane przez następujących stałych manifestu:

|Stała|Opis|
|-|-|
|`_A_ARCH`| Archiwum. Ustaw zawsze wtedy, gdy plik jest zmienione i obsadzona przez użycie polecenia BACKUP. Wartość: 0x20|
|`_A_HIDDEN`| Ukryty plik. Zwykle widoczne przy użyciu polecenia DIR, chyba że używana jest opcja /AH. Zwraca informacje o normalne pliki, a także plików za pomocą tego atrybutu. Wartość: 0x02|
|`_A_NORMAL`| Normalny. Plik można odczytać lub zapisywane bez ograniczeń. Wartość: 0x00|
|`_A_RDONLY`| Tylko do odczytu. Nie można otworzyć pliku do zapisu, a nie można utworzyć pliku o takiej samej nazwie. Wartość: 0x01|
|`_A_SUBDIR`| Podkatalog. Wartość: 0x10|
|`_A_SYSTEM`| System plików. Zwykle widoczne przy użyciu polecenia DIR, chyba że używana jest opcja /AS. Wartość: 0x04|

Kilka stałych, które można łączyć za pomocą operatora OR (&#124;).

## <a name="see-also"></a>Zobacz także

[Funkcje wyszukiwania nazwy pliku](../c-runtime-library/filename-search-functions.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
