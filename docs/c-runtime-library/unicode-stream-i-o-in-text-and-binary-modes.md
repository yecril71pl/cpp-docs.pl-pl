---
title: Strumień We/Wy Unicode w trybach tekstowym i binarnym
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: e54f29292ae9e202cf27c354374132dda267aff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469790"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Strumień We/Wy Unicode w trybach tekstowym i binarnym

Gdy Unicode strumienia procedury we/wy (takie jak **fwprintf —**, **fwscanf —**, **fgetwc —**, **fputwc —**, **fgetws —**, lub **fputws —**) działa na plik, który jest otwarty w trybie tekstowym (ustawienie domyślne), dwa rodzaje znak konwersje miejsce:

- Konwersja znaków Unicode do MBCS lub MBCS-Unicode. Kiedy funkcja strumienia we/wy Unicode działa w trybie tekstowym, źródła lub strumienia docelowego będzie traktowana jako sekwencja znaków wielobajtowych. W związku z tym, funkcje strumienia wejściowego Unicode konwertują znaki wielobajtowe do znaków dwubajtowych (tak jak w przypadku przez wywołanie **mbtowc** funkcji). Z tego samego powodu funkcje strumienia wyjściowego Unicode konwertują ciągi dwubajtowe na znaki wielobajtowe (tak jak w przypadku przez wywołanie **wctomb —** funkcji).

- Powrót karetki - tłumaczenia wysuwu wiersza (CR-LF). Tłumaczenie jest wcześniejsza niż MBCS - Unicode konwersji (w przypadku danych wejściowych funkcje strumienia Unicode) i po nim Unicode - konwersji MBCS (w przypadku funkcji dane wyjściowe strumienia Unicode). Podczas wprowadzania każdy znak powrotu karetki - kombinacja wysuwu wiersza jest tłumaczony na znak pojedynczego wysuwu wiersza. W danych wyjściowych każdy znak wysuwu wiersza jest tłumaczona na znak powrotu karetki - kombinacja wysuwu wiersza.

Jednak jeśli funkcja strumienia we/wy Unicode działa w trybie binarnym, plik będzie traktowana jako Unicode i bez konwersji tłumaczenia lub znakiem CR-LF wypada w danych wejściowych lub wyjściowych. Użyj _setmode — (_fileno (stdin), _O_BINARY); Instrukcja, aby można było prawidłowo używać wcin na plik tekstowy UNICODE.

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
