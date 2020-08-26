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
ms.openlocfilehash: 0b951fc76635f67115f4a832ed316d66b6de7497
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88836702"
---
# <a name="translation-mode-constants"></a>Tryb tłumaczenia — Stałe

## <a name="syntax"></a>Składnia

```
#include <fcntl.h>
```

## <a name="remarks"></a>Uwagi

`_O_BINARY` `_O_TEXT` Stałe manifestu i określają tryb tłumaczenia dla plików ( `_open` i `_sopen` ) lub trybu tłumaczenia strumieni ( `_setmode` ).

Dozwolone wartości to:

|Wartość|Opis|
|-|-|
`_O_TEXT`  | Otwiera plik w trybie tekstu (tłumaczone). Kombinacje powrotu karetki liniowej (CR-LF) są tłumaczone na pojedynczy znak wysuwu wiersza (LF) na wejściu. Znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W plikach otwartych do odczytu i do odczytu i zapisu program `fopen` sprawdza, czy Ctrl + Z na końcu pliku i usuwa go, jeśli jest to możliwe. Dzieje się tak, ponieważ używanie `fseek` `ftell` funkcji i do poruszania się w pliku kończącym się na klawiaturze Ctrl + z może spowodować `fseek` zachowanie nieprawidłowego końca pliku.
`_O_BINARY`  | Otwiera plik w trybie binarnym (nieprzetłumaczonym). Powyższe tłumaczenia są pomijane.
`_O_RAW`  | Analogicznie jak `_O_BINARY` . Obsługiwane w przypadku zgodności C 2,0.

Aby uzyskać więcej informacji, zobacz [plik tekstowy i tryb binarny we/wy](../c-runtime-library/text-and-binary-mode-file-i-o.md) oraz [tłumaczenie plików](../c-runtime-library/file-translation-constants.md).

## <a name="see-also"></a>Zobacz też

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_pipe](../c-runtime-library/reference/pipe.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_setmode](../c-runtime-library/reference/setmode.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
