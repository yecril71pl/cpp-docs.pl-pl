---
title: 'Unicode: zestaw znaków dwubajtowych'
description: Wprowadzenie do zestawu znaków Unicode w środowisku uruchomieniowym Microsoft C.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], wide character set
- wide characters [C++], Unicode
ms.assetid: b6a05a21-59a5-4d30-8c85-2dbe185f7a74
ms.openlocfilehash: 751017a62a960eaf2afa2354a43a13971b89252a
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590163"
---
# <a name="unicode-the-wide-character-set"></a>Unicode: zestaw znaków dwubajtowych

Znak dwubajtowy to kod 2-bitowy. Każdy znak używany w nowoczesnej skali na całym świecie, w tym symbole techniczne i znaki specjalne publikacji, można przedstawić na podstawie specyfikacji Unicode jako znaku dwubajtowego. Opracowane i utrzymywane przez duże konsorcjum, które obejmuje firmę Microsoft, standard Unicode jest teraz szeroko zaakceptowany.

Znak dwubajtowy jest typu **`wchar_t`** . Ciąg znaków dwubajtowych jest reprezentowany jako **`wchar_t[]`** Tablica. Wskaż tablicę `wchar_t*` wskaźnikiem. 

Można reprezentować dowolny znak ASCII jako znak dwubajtowy, tworząc prefiks litery `L` . Na przykład, `L'\0'` jest znakiem o zerowej szerokości (16-bitowym).

Można reprezentować dowolny literał ciągu ASCII jako literał ciągu znaków dwubajtowych, tworząc prefiks litery `L` . Na przykład `L"Hello"`.

Ogólnie rzecz biorąc, znaki dwubajtowe wykorzystują więcej miejsca w pamięci niż znaki wielodostępne. Ale szerokie znaki są szybsze do przetworzenia. Tylko jedno ustawienie regionalne może być reprezentowane jednocześnie w kodowaniu wielobajtowym. Wszystkie zestawy znaków na świecie są reprezentowane jednocześnie przez reprezentację w formacie Unicode.

## <a name="see-also"></a>Zobacz też

[Międzynarodowe](../c-runtime-library/internationalization.md)\
[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)
