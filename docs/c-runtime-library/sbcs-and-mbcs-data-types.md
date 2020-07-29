---
title: SBCS i MBCS — Typy danych
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 72215b7a3fff638daf02f136e3a107ce8a8a00d5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233915"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS i MBCS — Typy danych

Każda procedura biblioteki wykonawczej MBCS firmy Microsoft, która obsługuje tylko jeden znak wielobajtowy lub jeden bajt znaku wielobajtowego oczekuje **`unsigned int`** argumentu (gdzie 0x00 <= wartość znaku <= 0xFFFF i 0x00 <= wartość bajtowa <= 0xFF). Procedura MBCS, która obsługuje bajty wielobajtowe lub znaki w kontekście ciągu, oczekuje, że ciąg znaków wielobajtowych ma być reprezentowany jako **`unsigned char`** wskaźnik.

> [!CAUTION]
> Każdy bajt znaku wielobajtowego może być reprezentowany w 8-bitowym **`char`** . Jednak jeden jednobajtowy znak typu SBCS lub MBCS o **`char`** wartości większej niż 0x7F jest ujemny. Gdy taki znak jest konwertowany bezpośrednio do **`int`** lub a **`long`** , wynik jest podpisywany przez kompilator i w związku z tym może dać nieoczekiwane wyniki.

W związku z tym najlepszym rozwiązaniem jest reprezentowanie bajtu znaku wielobajtowego jako 8-bitowego **`unsigned char`** . Aby uniknąć negatywnego wyniku, po prostu Przekonwertuj znak jednobajtowy typu **`char`** na, **`unsigned char`** przed przekonwertowaniem go na **`int`** lub **`long`** .

Ponieważ niektóre funkcje obsługujące ciągi SBCS pobierają (podpisane) **`char`** <strong>\*</strong> Parametry, Ostrzeżenie kompilatora niezgodności typów spowoduje, że **_MBCS** jest zdefiniowana. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia, wymienione w kolejności wydajności:

1. Użyj funkcji wbudowanych w programie używanie TCHAR. C. Jest to zachowanie domyślne.

1. Używaj makr bezpośrednich w używanie TCHAR. H przez zdefiniowanie **_MB_MAP_DIRECT** w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typy. Jest to najszybszy Metoda, ale nie jest bezpieczna pod względem typów.

1. Użyj bezpiecznej, statycznie połączonej biblioteki funkcji w używanie TCHAR. C. Aby to zrobić, Zdefiniuj stałą **_NO_INLINING** w wierszu polecenia. Jest to najwolniejsza Metoda, ale najbardziej bezpieczna typ.

## <a name="see-also"></a>Zobacz także

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
