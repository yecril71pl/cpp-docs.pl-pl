---
title: We/Wy strumienia Unicode w trybach tekstowym i binarnym | Dokumenty Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b89ff3fc752901e9b3cf30c305110b387dc04562
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409056"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Strumień We/Wy Unicode w trybach tekstowym i binarnym

Gdy Unicode strumienia procedury we/wy (takich jak **fwprintf —**, **fwscanf —**, **fgetwc —**, **fputwc —**, **fgetws —**, lub **fputws —**) działa na pliku, która jest otwarta w trybie tekstowym (ustawienie domyślne), dwa rodzaje znaków konwersje miejsce:

- Konwersja Unicode do MBCS lub MBCS na Unicode. Jeśli funkcja strumienia I/O Unicode działa w trybie tekstowym, źródła lub strumień docelowy zakłada, że sekwencja znaków wielobajtowych. W związku z tym funkcji wejścia strumienia Unicode konwertuje znaki wielobajtowe na znaki dwubajtowe (tak jak w przypadku przez wywołanie do **mbtowc —** funkcji). Z tego samego powodu funkcje strumieni wyjściowych Unicode przekonwertować znaki dwubajtowe znaków wielobajtowych (tak jak w przypadku przez wywołanie do **wctomb —** funkcji).

- Powrót karetki - tłumaczenia wysuwu wiersza (CR LF). Tłumaczenie występuje przed MBCS — Konwersja Unicode (dla funkcji wejściowych strumienia Unicode) i po Unicode - konwersji MBCS (dla funkcji wyjściowego strumienia Unicode). Podczas wprowadzania danych przez każdego powrotu karetki - kombinacja wysuwu wiersza jest przetłumaczyć znaku pojedynczego wysuwu wiersza. W danych wyjściowych każdy znak wysuwu wiersza jest przetłumaczony na powrót karetki - kombinacja wysuwu wiersza.

Jednak jeśli funkcja strumienia I/O Unicode działa w trybie binarnym, plik zostanie potraktowany jako Unicode i brak konwersji tłumaczenia lub znak CR LF wypada w danych wejściowych lub wyjściowych. Użyj _setmode — (_fileno — (stdin), _o_binary —); instrukcji, aby można było poprawnie używać wcin w pliku tekstowym UNICODE.

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)<br/>
