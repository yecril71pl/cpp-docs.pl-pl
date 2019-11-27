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
ms.openlocfilehash: 5821048363d92911f2902a580cb11f5b349f5e7c
ms.sourcegitcommit: 4f15b69e35dd112001b24fe9dc836dd5d6902465
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474068"
---
# <a name="locales-and-code-pages"></a>Ustawienia regionalne i strony kodowe

Identyfikator ustawień regionalnych odzwierciedla konwencje i język lokalny dla określonego regionu geograficznego. Dany język może być mówiony w więcej niż jednym kraju/regionie; na przykład, portugalski jest mówiony w Brazylii, jak również w Portugalii. Z drugiej strony kraj/region mogą mieć więcej niż jeden język urzędowy. Na przykład Kanada ma dwa języki: angielski i francuski. W tym przypadku Kanada ma dwie odrębne ustawienia regionalne: kanadyjski — angielski i kanadyjski — francuski. Niektóre kategorie zależne od ustawień regionalnych obejmują formatowanie dat i format wyświetlania wartości pieniężnych.

Język określa konwencje formatowania tekstu i danych, podczas gdy kraj/region określa konwencje lokalne. Każdy język ma unikatowe mapowanie reprezentowane przez strony kodowe, które zawierają znaki inne niż te w alfabecie (takie jak znaki interpunkcyjne i cyfry). Strona kodowa jest zestawem znaków i jest powiązany z językiem. W związku z tym [ustawieniem regionalnym](../c-runtime-library/locale.md) jest unikatowa kombinacja języka, kraju/regionu i strony kodowej. Ustawienia regionalne i strony kodowej można zmienić w czasie wykonywania, wywołując funkcję [setlocaling](../c-runtime-library/reference/setlocale-wsetlocale.md) .

Różne języki mogą korzystać z różnych stron kodowych. Na przykład strona kodowa ANSI 1252 jest używana w języku angielskim i większości języków europejskich, a strona kodowa ANSI 932 jest używana dla japońskiego Kanji. Praktycznie wszystkie strony kodowe współużytkują zestaw znaków ASCII dla najniższych znaków 128 (0x00 do 0x7F).

Każda jednobajtowa strona kodowa może być reprezentowana w tabeli (z wpisami 256) jako mapowanie wartości bajtowych na znaki (w tym cyfry i znaki interpunkcyjne) lub symbole. Każda strona kodowa wielobajtowego może być również reprezentowana jako bardzo duża tabela (z wpisami o rozmiarze 64 KB) wartości dwubajtowych do znaków. W tej rzeczywistości jest to zwykle reprezentowane jako tabela dla pierwszych 256 (jednobajtowych) znaków i jako zakresy wartości dwubajtowych.

Aby uzyskać więcej informacji na temat stron kodowych, zobacz [strony kodowe](../c-runtime-library/code-pages.md).

Biblioteka wykonawcza C ma dwa typy wewnętrznych stron kodowych: locale i wielobajtowe. Bieżącą stronę kodową można zmienić podczas wykonywania programu (zobacz dokumentację funkcji [setlocals](../c-runtime-library/reference/setlocale-wsetlocale.md) i [_setmbcp](../c-runtime-library/reference/setmbcp.md) ). Ponadto Biblioteka wykonawcza może uzyskać i używać wartości strony kodowej systemu operacyjnego, która jest stała na czas trwania wykonywania programu.

Gdy zmienia się Strona kodowa ustawień regionalnych, zachowanie zestawu funkcji zależnych od ustawień regionalnych zmienia się na ten, który jest określany przez wybraną stronę kodową. Domyślnie wszystkie funkcje zależne od ustawień regionalnych rozpoczynają wykonywanie z użyciem strony kodowej ustawień regionalnych unikatowych dla ustawień regionalnych "C". Można zmienić wewnętrzną stronę kodową ustawień regionalnych (a także inne właściwości specyficzne dla ustawień regionalnych), wywołując funkcję `setlocale`. Wywołanie `setlocale`(LC_ALL, "") ustawia ustawienia regionalne wskazane przez ustawienia regionalne użytkownika systemu operacyjnego.

Podobnie, gdy zmienia się Strona kodowa wielobajtowego, zachowanie funkcji wielobajtowych zmienia się na, która jest podyktowana przez wybraną stronę kodową. Domyślnie wszystkie funkcje wielobajtowe zaczynają wykonywanie ze stroną kodową wielobajtowym odpowiadającym domyślnej stronie kodowej systemu operacyjnego. Wewnętrzną stronę kodową wielobajtową można zmienić, wywołując funkcję `_setmbcp`.

Funkcja C Run-Time `setlocale` ustawia, zmienia lub wysyła zapytania do niektórych lub wszystkich informacji o ustawieniach regionalnych bieżącego programu. Procedura [_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) to dwubajtowa wersja `setlocale`; argumenty i wartości zwracane `_wsetlocale` są ciągami znaków dwubajtowych.

## <a name="see-also"></a>Zobacz także

[Unicode i MBCS](../text/unicode-and-mbcs.md)<br/>
[Zalety przenośności zestawu znaków](../text/benefits-of-character-set-portability.md)
