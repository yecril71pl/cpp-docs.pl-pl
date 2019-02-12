---
title: Znaki dwubajtowe
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151965"
---
# <a name="wide-characters"></a>Znaki dwubajtowe

**ANSI 3.1.3.4** wartość stałej znakowej liczba całkowita, która zawiera więcej niż jeden znak lub stałą znaku dwubajtowego, który zawiera więcej niż jeden znak wielobajtowy

Zwykły znak stałej, "ab" ma wartość całkowitą (int) 0x6162. W przypadku więcej niż jednego bajtu poprzednio odczytać bajtów są przesuwane w lewo przez wartość **CHAR_BIT** i następny bajt jest porównywany z małą ilością za pomocą operatora bitowego OR **CHAR_BIT** usługi bits. Liczba bajtów w stałych znaków wielobajtowych nie może przekraczać sizeof(int), który jest 4-kod docelowy 32-bitowych.

Zgodnie z powyższym stałych znaków wielobajtowych do odczytu i to jest konwertowana na stałych znaków dwubajtowych za pośrednictwem `mbtowc` funkcji czasu wykonywania. Jeśli wynik nie jest prawidłową stałą znaku dwubajtowego, zgłaszany jest błąd. W każdym przypadku liczba bajtów zbadane przez `mbtowc` funkcja jest ograniczona do wartości `MB_CUR_MAX`.

## <a name="see-also"></a>Zobacz także

[Znaki](../c-language/characters.md)
