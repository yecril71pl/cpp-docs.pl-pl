---
title: SBCS i MBCS — Typy danych
description: Jak reprezentować znaki pojedyncze i wielobajtowe w środowisku uruchomieniowym języka Microsoft C.
ms.topic: conceptual
ms.date: 04/11/2018
f1_keywords:
- MBCS
- SBCS
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
ms.openlocfilehash: 27d32ffd079cdc82ab8a799df9d9ec778b546a3b
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590254"
---
# <a name="sbcs-and-mbcs-data-types"></a>SBCS i MBCS — Typy danych

Jakakolwiek procedura biblioteki wykonawczej MBCS firmy Microsoft, która obsługuje tylko 1 znak wielobajtowy lub 1 bajt znaku wielobajtowego oczekuje **`unsigned int`** argumentu (gdzie 0x00 <= wartość znaku <= 0xFFFF i 0x00 <= wartość bajtowa <= 0xFF). Procedura MBCS, która obsługuje bajty wielobajtowe lub znaki w kontekście ciągu, oczekuje, że ciąg znaków wielobajtowych ma być reprezentowany jako **`unsigned char`** wskaźnik.

> [!CAUTION]
> Każdy bajt znaku wielobajtowego może być reprezentowany w 8-bitowym **`char`** . Jednak jeden jednobajtowy znak typu SBCS lub MBCS o **`char`** wartości większej niż 0x7F jest ujemny. Gdy taki znak jest konwertowany bezpośrednio do **`int`** lub a **`long`** , wynik jest podpisywany przez kompilator i w związku z tym może dać nieoczekiwane wyniki.

Najlepiej reprezentuje bajt znaku wielobajtowego jako 8-bitowy **`unsigned char`** . Lub, aby uniknąć negatywnego wyniku, **`char`** **`unsigned char`** przed przekonwertowaniem go na **`int`** lub **`long`** .

Ponieważ niektóre funkcje obsługujące ciągi SBCS pobierają (podpisane) **`char`** <strong>\*</strong> Parametry, Ostrzeżenie kompilatora niezgodności typów spowoduje, że **_MBCS** jest zdefiniowana. Istnieją trzy sposoby, aby uniknąć tego ostrzeżenia, wymienione w kolejności wydajności:

1. Używaj funkcji wbudowanych bezpiecznie typu w używanie TCHAR. H. Jest to zachowanie domyślne.

1. Używaj makr bezpośrednich w używanie TCHAR. H przez zdefiniowanie **_MB_MAP_DIRECT** w wierszu polecenia. Jeśli to zrobisz, musisz ręcznie dopasować typy. Jest to najszybszy Metoda, ale nie jest bezpieczna pod względem typów.

1. Użyj bezpiecznej, statycznie połączonej biblioteki funkcji w używanie TCHAR. H. Aby to zrobić, Zdefiniuj stałą **_NO_INLINING** w wierszu polecenia. Jest to najwolniejsza Metoda, ale najbardziej bezpieczna typ.

## <a name="see-also"></a>Zobacz też

[Internacjonalizacja](../c-runtime-library/internationalization.md)<br/>
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
