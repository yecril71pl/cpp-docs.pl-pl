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
ms.openlocfilehash: 18e0ad8615bbe89c265247041729027f661915fe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62304387"
---
# <a name="translation-mode-constants"></a>Tryb tłumaczenia — Stałe

## <a name="syntax"></a>Składnia

```
#include <fcntl.h>
```

## <a name="remarks"></a>Uwagi

`_O_BINARY` i `_O_TEXT` stałych manifestu określić tryb translacji dla plików (`_open` i `_sopen`) lub tryb translacji dla strumieni (`_setmode`).

Dozwolone wartości to:

|||
|-|-|
`_O_TEXT`  | Otwiera plik w trybie tekstowym (tłumaczonym). Karetki - kombinacji (CR-LF) wysuwu wiersza są tłumaczone na jednym wysuwu wiersza (LF) na dane wejściowe. Znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu lub odczytu/zapisu `fopen` wyszukuje klawisze CTRL + Z, na końcu pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa `fseek` i `ftell` może spowodować, że funkcje, aby przenieść w pliku kończy się znakiem CRTL + Z `fseek` działać nieprawidłowo w pobliżu końca pliku.
`_O_BINARY`  | Otwiera plik w trybie binarnym (nieprzetłumaczonym). Powyższe tłumaczenia są pomijane.
`_O_RAW`  | Taki sam jak `_O_BINARY`. Obsługiwane w przypadku zgodności C w wersji 2.0.

Aby uzyskać więcej informacji, zobacz [tekstowych i binarnych We/Wy trybu](../c-runtime-library/text-and-binary-mode-file-i-o.md) i [tłumaczenia pliku](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Zobacz także

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
