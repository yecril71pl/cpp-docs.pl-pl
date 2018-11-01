---
title: Ustawienia regionalne i strony kodowe
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: 0015e0a7a81abbd3472a8c845a9b8c0d8caf4618
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610541"
---
# <a name="locales-and-code-pages"></a>Ustawienia regionalne i strony kodowe

Identyfikator ustawień regionalnych odzwierciedla konwencje lokalnych i język w określonym regionie geograficznym. Danego języka, może być używany w więcej niż jednego kraju/regionu; na przykład portugalski jest używany w Brazylii, jak również jak Portugalii. Z drugiej strony kraj/region może mieć więcej niż jeden oficjalnego języka. Na przykład, Kanada, ma dwa języki: języka angielskiego i francuskiego. W związku z tym, Kanada, ma dwa różne ustawienia regionalne: kanadyjski angielski i francuski (kanadyjski). Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych.

Określa język, tekstu i formatowania Konwencji, podczas gdy kraj/region określa konwencje lokalnych danych. Każdy język ma unikatowe mapowania, reprezentowane przez stron kodowych, w tym znaki inne niż te w alfabecie (na przykład znaków interpunkcyjnych i cyfry). Strona kodowa jest zestawem znaków i jest powiązany z językiem. W efekcie [ustawień regionalnych](../c-runtime-library/locale.md) to unikatowa kombinacja język, kraj/region i stronę kodową. Można zmienić ustawienie strony ustawień regionalnych i kodu w czasie wykonywania przez wywołanie metody [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkcji.

Różne strony kodowe użyć różnych językach. Na przykład strona kodowa ANSI 1252 jest używana w języku angielskim i większość języków europejskich i stronę kodową ANSI 932 służy do japoński Kanji. Praktycznie wszystkich stron kodowych udostępnić zestaw znaków ASCII dla najniższej 128 znaków (0x00 0x7F).

Wszystkie strony kodowej pojedynczych bajtów może być reprezentowany w tabeli (z wpisy 256) jako mapowanie wartości bajtu znaków (łącznie z cyfr i znaków interpunkcyjnych) lub symbole. Dowolnej strony kodowe wielobajtowe również może być reprezentowany jako tabelę bardzo duże (z wpisy 64 KB) wartości dwubajtowych znaków. W praktyce jednak ją są zwykle reprezentowany jako tabelę dla pierwszych 256 znaków (pojedynczych bajtów), a zakresy dla wartości dwubajtowych.

Aby uzyskać więcej informacji dotyczących stron kodowych, zobacz [stron kodowych](../c-runtime-library/code-pages.md).

Biblioteki wykonawczej C ma dwa typy stron kodowych wewnętrzny: ustawienia regionalne i znaków wielobajtowych. Można zmienić bieżącej stronie kodowej, podczas wykonywania programu (zajrzyj do dokumentacji [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) i [_setmbcp](../c-runtime-library/reference/setmbcp.md) funkcji). Ponadto biblioteki wykonawczej może uzyskać i używana wartość strony kodowej systemu operacyjnego, który jest stały czas trwania wykonywania programu.

Strona kodowa ustawień lokalnych zmiany, zachowanie zależne od ustawień regionalnych zbiór funkcji zmiany, definiowane przez stronę kodową wybrany. Domyślnie wszystkie funkcje zależne od ustawień regionalnych rozpocząć wykonywania za pomocą strona kodowa ustawień lokalnych unikatowe dla ustawień regionalnych "C". Możesz zmienić stronę kodową wewnętrznego ustawienia regionalne (a także inne właściwości specyficzne dla ustawień regionalnych) przez wywołanie metody `setlocale` funkcji. Wywołanie `setlocale`(LC_ALL, "") ustawia ustawienia regionalne, wskazywanym przez ustawienia regionalne użytkownika systemu operacyjnego.

Podobnie, po wielobajtowa strona kodowa zmienia zachowanie wielobajtowych funkcji zmiany, definiowane przez stronę kodową wybrany. Domyślnie wszystkie funkcje wielobajtowych zaczyna się od wykonania stronę kodu wielobajtowego, odpowiadający systemowi operacyjnemu domyślną stroną kodową. Można zmienić wewnętrznych wielobajtowa strona kodowa przez wywołanie metody `_setmbcp` funkcji.

Funkcja środowiska wykonawczego języka C `setlocale` Ustawia, zmiany lub zapytania, niektórych lub wszystkich informacji o ustawieniach regionalnych bieżącego programu. [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) procedura jest wersją znaków dwubajtowych `setlocale`; argumenty i wartości zwracane `_wsetlocale` są ciągami znaków dwubajtowych.

## <a name="see-also"></a>Zobacz też

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Zalety przenośności zestawu znaków](../text/benefits-of-character-set-portability.md)