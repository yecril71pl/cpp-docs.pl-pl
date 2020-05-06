---
title: Znaki dwubajtowe
ms.date: 11/04/2016
helpviewer_keywords:
- wide characters
ms.assetid: 165c4a12-8ab9-45fb-9964-c55e9956194c
ms.openlocfilehash: 868acf0abd26a1f4b5533bb997fb9ea09a27954b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291005"
---
# <a name="wide-characters"></a>Znaki dwubajtowe

**3.1.3.4 ANSI** Wartość stałej znakowej liczby całkowitej, która zawiera więcej niż jeden znak lub stałą znakową, która zawiera więcej niż jeden znak wielobajtowy.

Zwykła stała znakowa, "AB" ma wartość całkowitą (int) 0x6162. W przypadku więcej niż jednego bajtu poprzednio odczytane bajty są przesunięte w lewo o wartość **CHAR_BIT** a następny bajt jest porównywany przy użyciu operatora bitowego lub z niską **CHAR_BIT** bitów. Liczba bajtów w stałej znakowej wielobajtowej nie może przekroczyć sizeof (int), która jest 4 dla kodu docelowego 32-bitowego.

Stała znaku wielobajtowego jest odczytywana jak powyżej i jest konwertowana na stałą o szerokim znaku przy `mbtowc` użyciu funkcji run-time. Jeśli wynik nie jest prawidłową stałą znaków dwubajtowych, zostanie wygenerowany błąd. W każdym przypadku liczba bajtów badanych przez `mbtowc` funkcję jest ograniczona do wartości. `MB_CUR_MAX`

## <a name="see-also"></a>Zobacz też

[Znaków](../c-language/characters.md)
