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
ms.openlocfilehash: 10f77c7142c707d4df841899b50be2807b1b9c7f
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376275"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Strumień We/Wy Unicode w trybach tekstowym i binarnym

Gdy procedura we/wy strumienia Unicode (taka jak **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws**lub **fputws**) działa na pliku otwartym w trybie tekstowym (ustawienie domyślne), wykonywane są dwa rodzaje konwersji znaków:

- Konwersja z formatu Unicode na MBCS lub MBCS na Unicode. Gdy funkcja strumienia Unicode we/wy działa w trybie tekstowym, zakłada się, że strumień źródłowy lub docelowy jest sekwencją znaków wielobajtowych. W związku z tym funkcje wejściowe strumienia Unicode konwertują znaki wielobajtowe na znaki szerokie (jak w przypadku wywołania funkcji **mbtowc** ). Z tego samego powodu funkcje strumienia Unicode-Output przekonwertują szerokie znaki na znaki wielobajtowe (jak w przypadku wywołania funkcji **wctomb** ).

- Tłumaczenie znaku wysuwu wiersza (CR-LF). To tłumaczenie występuje przed konwersją MBCS-Unicode (dla funkcji wejściowych strumienia Unicode) i po konwersji Unicode-MBCS (dla funkcji wyjściowych strumienia Unicode). Podczas wprowadzania każda kombinacja wysuwu wiersza powrotu karetki jest tłumaczona na pojedynczy znak wysuwu wiersza. Podczas wyprowadzania każdy znak wysuwu wiersza jest tłumaczony na kombinację wysuwu wiersza powrotu karetki.

Jeśli jednak funkcja strumienia Unicode we/wy działa w trybie binarnym, zakłada się, że plik jest w formacie Unicode i nie ma żadnego tłumaczenia CR-LF ani konwersji znaków podczas wejścia lub wyjścia. Użyj instrukcji `_setmode( _fileno( stdin ), _O_BINARY );` , aby prawidłowo użyć `wcin` pliku tekstowego w formacie Unicode.

## <a name="see-also"></a>Zobacz także

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
