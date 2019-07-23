---
title: Tryb tłumaczenia — Stałe
ms.date: 11/04/2016
f1_keywords:
- _O_BINARY
- _O_TEXT
- _O_RAW
helpviewer_keywords:
- O_BINARY constant
- O_TEXT constant
- O_RAW constant
- _O_TEXT constant
- _O_RAW constant
- translation constants
- _O_BINARY constant
- translation, constants
- translation, modes
- translation modes (file I/O)
ms.assetid: a5993bf4-7e7a-47f9-83c3-e46332b85579
ms.openlocfilehash: a86c0c1a0b70613c6e7749c78f58f6dfb3602d4d
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376278"
---
# <a name="translation-mode-constants"></a>Tryb tłumaczenia — Stałe

## <a name="syntax"></a>Składnia

```
#include <fcntl.h>
```

## <a name="remarks"></a>Uwagi

`_open` `_setmode` `_sopen`Stałe manifestu `_O_TEXT` i określają tryb tłumaczenia dla plików (i) lub trybu tłumaczenia strumieni (). `_O_BINARY`

Dozwolone wartości to:

|||
|-|-|
`_O_TEXT`  | Otwiera plik w trybie tekstu (tłumaczone). Kombinacje powrotu karetki liniowej (CR-LF) są tłumaczone na pojedynczy znak wysuwu wiersza (LF) na wejściu. Znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W plikach otwartych do odczytu i do odczytu i zapisu program `fopen` sprawdza, czy Ctrl + Z na końcu pliku i usuwa go, jeśli jest to możliwe. Dzieje się tak, ponieważ używanie `fseek` funkcji `ftell` i do poruszania się w pliku kończącym się na klawiaturze `fseek` Ctrl + z może spowodować zachowanie nieprawidłowego końca pliku.
`_O_BINARY`  | Otwiera plik w trybie binarnym (nieprzetłumaczonym). Powyższe tłumaczenia są pomijane.
`_O_RAW`  | Analogicznie `_O_BINARY`jak. Obsługiwane w przypadku zgodności C 2,0.

Aby uzyskać więcej informacji, zobacz [plik tekstowy i tryb binarny we/wy](../c-runtime-library/text-and-binary-mode-file-i-o.md) oraz [tłumaczenie plików](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Zobacz także

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
