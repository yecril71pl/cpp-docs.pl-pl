---
title: Stałe tłumaczenia pliku
ms.date: 11/04/2016
helpviewer_keywords:
- translation constants
- file translation [C++], constants
- translation, file translation constants
- translation, constants
- constants [C++], file translation mode
- file translation [C++]
ms.assetid: 49b13bf3-442e-4d19-878b-bd1029fa666a
ms.openlocfilehash: 363d95e744ccdb45cf06b8303ae4b60c9ecd58c1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443261"
---
# <a name="file-translation-constants"></a>Stałe tłumaczenia pliku

## <a name="syntax"></a>Składnia

```
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

Te stałe określają tryb tłumaczenia ( **"b"** lub **"t"** ). Tryb jest dołączony do ciągu określającego typ dostępu ( **"r"** , **"w"** , **"a"** , **"r +"** , **"w +"** , **"a +"** ).

Tryby tłumaczenia są następujące:

- **&**

   Otwiera w trybie tekst (przetłumaczony). W tym trybie kombinacje wysuwu wiersza (CR-LF) są tłumaczone na znaki wysuwu wiersza (LF) na wejściu, a sygnały LF są tłumaczone na kombinacje CR-LF w danych wyjściowych. Ponadto CTRL + Z jest interpretowany jako znak końca pliku na wejściu. W plikach otwartych do odczytu lub odczytu i zapisu, `fopen` sprawdza, czy CTRL + Z na końcu pliku i usuwa go, jeśli to możliwe. Dzieje się tak, ponieważ używanie funkcji `fseek` i `ftell` do przenoszenia plików kończących się na klawiaturze CTRL + Z może spowodować, że `fseek` zachować niewłaściwie blisko końca pliku.

   > [!NOTE]
   > Opcja **t** nie jest częścią standardu ANSI dla `fopen` i `freopen`. Jest to rozszerzenie firmy Microsoft i nie powinno być używane w przypadku potrzeby przenoszenia w formacie ANSI.

- **b**

   Otwiera w trybie binarnym (nieprzetłumaczonym). Powyższe tłumaczenia są pomijane.

Jeśli **t** lub **b** nie jest określony w *trybie*, tryb tłumaczenia jest definiowany przez zmienną trybu domyślnego [_fmode](../c-runtime-library/fmode.md). Aby uzyskać więcej informacji na temat używania trybów tekstowych i binarnych, zobacz [plik tekstowy i tryb binarny we/wy](../c-runtime-library/text-and-binary-mode-file-i-o.md).

## <a name="see-also"></a>Zobacz też

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
