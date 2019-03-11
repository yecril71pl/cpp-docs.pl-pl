---
title: Stałe tłumaczenia pliku
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: ef9b986753de05c45b3071e55f9b163fa5a6a7da
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743331"
---
# <a name="file-translation-constants"></a>Stałe tłumaczenia pliku

## <a name="syntax"></a>Składnia

```
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

Te stałe określić tryb translacji (**"b"** lub **"t"**). Tryb znajduje się w ciąg określający typ dostępu (**"r"**, **"w"**, **""**, **"r +"**, **"w +"**, **"+"**).

Tryby tłumaczenia są następujące:

- **t**

   Zostanie otwarty w trybie tekstowym (tłumaczonym). W tym trybie kombinacji (CR-LF) powrotu karetki return/wysuwu wiersza są tłumaczone na jednym znaki wysuwu wiersza (LF) na dane wejściowe, a znaki wysuwu wiersza są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W przypadku plików otwartych do odczytu lub odczytu/zapisu `fopen` wyszukuje klawisze CTRL + Z, na końcu pliku i usuwa go, jeśli jest to możliwe. Odbywa się, ponieważ używa `fseek` i `ftell` może spowodować, że funkcje, aby przenieść w pliku kończy się znakiem CRTL + Z `fseek` działać nieprawidłowo w pobliżu końca pliku.

   > [!NOTE]
   > **t** opcja nie jest częścią standardu ANSI `fopen` i `freopen`. Jest rozszerzeniem firmy Microsoft i nie powinna być używana gdzie pożądana jest przenośność kodowania ANSI.

- **b**

   Zostanie otwarty w trybie binarnym (nieprzetłumaczonym). Powyższe tłumaczenia są pomijane.

Jeśli **t** lub **b** nie jest podana w *tryb*, tryb translacji jest zdefiniowany przez zmienną trybu domyślnego [_fmode](../c-runtime-library/fmode.md). Aby uzyskać więcej informacji na temat używania w trybach tekstowym i binarnym, zobacz [tekstowych i binarnych We/Wy trybu](../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="see-also"></a>Zobacz także

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
