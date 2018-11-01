---
title: _set_controlfp
ms.date: 04/05/2018
apiname:
- _set_controlfp
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- set_controlfp
- _set_controlfp
helpviewer_keywords:
- set_controlfp function
- floating-point functions, setting control word
- _set_controlfp function
ms.assetid: e0689d50-f68a-4028-a9c1-fb23eedee4ad
ms.openlocfilehash: 1187502f09849d7ca4d8e595c237cfa511d00c6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50499044"
---
# <a name="setcontrolfp"></a>_set_controlfp

Ustawia słowo sterujące zmiennoprzecinkowe.

## <a name="syntax"></a>Składnia

```C
void __cdecl _set_controlfp(
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parametry

*newControl*<br/>
Nowe wartości bitowe słowa sterującego.

*Maska*<br/>
Maska dla nowych bitów słowa kontrolującego do ustawienia.

## <a name="return-value"></a>Wartość zwracana

Brak.

## <a name="remarks"></a>Uwagi

**_Set_controlfp —** funkcji jest podobne do **_control87 —**, ale tylko ustawia słowo sterujące zmiennoprzecinkowe *newControl*. Bity w wartości wskazują stan sterowania zmiennoprzecinkowego. Stan sterowania zmiennoprzecinkowego umożliwia program do zmiany precyzji, zaokrąglania oraz trybu nieskończoności w pakiecie zmiennoprzecinkowym zapisu matematycznego. Można również zamaskowania lub usunięcia wyjątki zmiennoprzecinkowe przy użyciu **_set_controlfp —**. Aby uzyskać więcej informacji, zobacz [_control87 —, _controlfp, \__control87_2](control87-controlfp-control87-2.md).

Ta funkcja jest przestarzała, podczas kompilowania za pomocą [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md) ponieważ środowisko uruchomieniowe języka wspólnego obsługuje tylko domyślną precyzję zmiennoprzecinkową.

## <a name="requirements"></a>Wymagania

|Procedura|Wymagany nagłówek|Zgodność|
|-------------|---------------------|-------------------|
|**_set_controlfp**|\<float.h>|x86 tylko procesora|

Aby uzyskać więcej informacji na temat zgodności, zobacz [zgodności](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Obsługa liczb zmiennoprzecinkowych](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
