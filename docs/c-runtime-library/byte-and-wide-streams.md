---
title: Strumienie Byte oraz szerokie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e031aa0ebbad279c630f2687457af11dc478b72d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095836"
---
# <a name="byte-and-wide-streams"></a>Strumienie byte oraz szerokie

Strumień bajtów traktuje plik jako sekwencja bajtów. W ramach programu strumień jest taka sama sekwencja bajtów.

Z drugiej strony szeroki strumienia traktuje plik jako sekwencja uogólnionego znaków wielobajtowych, które mogą mieć szerokiej gamy reguły kodowania. (Pliki tekstowe i binarne są nadal Odczyt i zapisywane w sposób opisany wcześniej.) W ramach programu strumień wygląda odpowiedniej sekwencji znaków dwubajtowych. Występują konwersje między dwoma reprezentacje w ramach standardowej biblioteki C. Reguły konwersji można w zasadzie można zmienić za pomocą wywołania [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) , zmieniania kategorii `LC_CTYPE`. Każdego strumienia szerokiego określa jego reguły konwersji w czasie, staje się szeroki obiektowe i zachowuje te zasady, nawet jeśli kategoria `LC_CTYPE` zmienia się później.

Położenie w obrębie szerokiej strumienia niska te same ograniczenia, jak w przypadku steams tekstu. Ponadto wskaźnik pozycji pliku również może mieć do czynienia z kodowaniem zależnej od stanu. Zazwyczaj zawiera zarówno bajtów, przesunięcie w strumieniu i obiektu typu `mbstate_t`. W związku z tym, tylko niezawodne sposobem uzyskania położenie pliku, w ramach szerokiej strumienia jest przez wywołanie metody [fgetpos](../c-runtime-library/reference/fgetpos.md), a tylko niezawodny sposób, aby przywrócić pozycji uzyskane w ten sposób to przez wywołanie metody [fsetpos](../c-runtime-library/reference/fsetpos.md).

## <a name="see-also"></a>Zobacz też

[Pliki i strumienie](../c-runtime-library/files-and-streams.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)