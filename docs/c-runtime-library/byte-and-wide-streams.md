---
title: Strumienie byte oraz szerokie
description: Omówienie strumieni bajtów w bibliotece środowiska uruchomieniowego Microsoft C.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
ms.openlocfilehash: 38949206e65ff84836b9a3e83b78723adfe30582
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590280"
---
# <a name="byte-and-wide-streams"></a>Strumienie byte oraz szerokie

Strumień bajtów traktuje plik jako sekwencję bajtów. W ramach programu strumień jest identyczną sekwencją bajtów.

Z kolei szeroki strumień traktuje plik jako sekwencję uogólnionych znaków wielobajtowych, które mogą mieć szeroką gamę reguł kodowania. (Pliki tekstowe i binarne są nadal odczytywane i zapisywane zgodnie z opisem wcześniej). W ramach programu strumień wygląda podobnie do odpowiedniej sekwencji znaków dwubajtowych. Konwersje między dwiema reprezentacjami odbywają się w standardowej bibliotece C. Reguły konwersji mogą być w zasadzie modyfikowane przez wywołanie metody [setlocaling](../c-runtime-library/reference/setlocale-wsetlocale.md) , która zmienia kategorię `LC_CTYPE` . Każdy strumień panoramiczny określa reguły konwersji w czasie, gdy stają się zorientowane na szeroką skalę i zachowuje te reguły nawet wtedy, gdy Kategoria `LC_CTYPE` ulega zmianie.

Pozycjonowanie w strumieniu szerokim ma takie same ograniczenia jak dla pary tekstu. Ponadto wskaźnik położenia pliku może być również konieczny do zajmowania się kodowaniem zależnym od stanu. Zazwyczaj obejmuje przesunięcie bajtów w strumieniu i obiekt typu `mbstate_t` . W ten sposób Jedynym niezawodnym sposobem uzyskania pozycji w pliku w ramach całego strumienia jest wywołanie [fgetpos](../c-runtime-library/reference/fgetpos.md), a jedyną niezawodną metodą przywrócenia pozycji uzyskaną w ten sposób jest wywołanie [fsetpos](../c-runtime-library/reference/fsetpos.md).

## <a name="see-also"></a>Zobacz też

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)
