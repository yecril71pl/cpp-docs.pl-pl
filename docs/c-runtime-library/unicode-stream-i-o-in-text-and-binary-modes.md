---
title: Strumień We/Wy Unicode w trybach tekstowym i binarnym
description: Opis konwersji znaków za pomocą operacji we/wy strumienia Unicode.
ms.topic: conceptual
ms.date: 11/04/2016
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: 9c4ef7da54463021f9487849df0235ae289e38fa
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590241"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Strumień We/Wy Unicode w trybach tekstowym i binarnym

Gdy procedura we/wy strumienia Unicode (taka jak **fwprintf**, **fwscanf**, **fgetwc**, **fputwc**, **fgetws**lub **fputws**) działa na pliku otwartym w trybie tekstowym (ustawienie domyślne), wykonywane są dwa rodzaje konwersji znaków:

- Konwersja z formatu Unicode na MBCS lub MBCS na Unicode. Gdy funkcja strumienia Unicode we/wy działa w trybie tekstowym, zakłada się, że strumień źródłowy lub docelowy jest sekwencją znaków wielobajtowych. W związku z tym funkcje wejściowe strumienia Unicode konwertują znaki wielobajtowe na znaki szerokie (jak w przypadku wywołania funkcji **mbtowc** ). Z tego samego powodu funkcje strumienia Unicode-Output przekonwertują szerokie znaki na znaki wielobajtowe (jak w przypadku wywołania funkcji **wctomb** ).

- Tłumaczenie znaku wysuwu wiersza (CR-LF). To tłumaczenie występuje przed konwersją MBCS-Unicode (dla funkcji wejściowych strumienia Unicode) i po konwersji Unicode-MBCS (dla funkcji wyjściowych strumienia Unicode). Podczas wprowadzania każda kombinacja wysuwu wiersza powrotu karetki jest tłumaczona na pojedynczy znak wysuwu wiersza. Podczas wyprowadzania każdy znak wysuwu wiersza jest tłumaczony na kombinację wysuwu wiersza powrotu karetki.

Jeśli jednak funkcja strumienia Unicode we/wy działa w trybie binarnym, zakłada się, że plik jest w formacie Unicode i nie ma żadnego tłumaczenia CR-LF ani konwersji znaków podczas wejścia lub wyjścia. Użyj `_setmode( _fileno( stdin ), _O_BINARY );` instrukcji, aby prawidłowo użyć `wcin` pliku tekstowego w formacie Unicode.

## <a name="see-also"></a>Zobacz też

[Procedury środowiska uruchomieniowego języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Wejście i wyjście](../c-runtime-library/input-and-output.md)<br/>
