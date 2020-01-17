---
title: __argc, __argv, __wargv
description: Opisuje stałe globalne biblioteki środowiska uruchomieniowego Microsoft C __argc, __argvi __wargv.
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 86a22a7391c7bde34d7734631a2970a45851dda3
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123984"
---
# <a name="opno-loc__argc-opno-loc__argv-opno-loc__wargv"></a>__argc, __argv, __wargv

Zmienna globalna `__argc` jest liczbą argumentów wiersza polecenia przekazaną do programu. `__argv` jest wskaźnikiem do tablicy ciągów o pojedynczym bajcie lub wielobajtowym znakiem, które zawierają argumenty programu, a `__wargv` jest wskaźnikiem do tablicy ciągów o szerokim znaku, które zawierają argumenty programu. Te zmienne globalne zapewniają argumenty do `main` lub `wmain`.

## <a name="syntax"></a>Składnia

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Uwagi

W programie, który używa funkcji `main`, `__argc` i `__argv` są inicjowane podczas uruchamiania programu przy użyciu wiersza polecenia, który służy do uruchamiania programu. Wiersz polecenia jest analizowany w poszczególnych argumentach, a symbole wieloznaczne są rozwinięte. Liczba argumentów jest przypisana do `__argc`, a ciągi argumentów są przydzielane na stercie, a wskaźnik do tablicy argumentów jest przypisany do `__argv`. W programie skompilowanym do używania znaków dwubajtowych i funkcji `wmain`, argumenty są analizowane, a symbole wieloznaczne są rozwinięte jako ciągi o szerokim znaku, a wskaźnik do tablicy ciągów argumentów jest przypisany do `__wargv`.

W przypadku kodu przenośnego zalecamy używanie argumentów przekazane do `main`, aby uzyskać argumenty wiersza polecenia w programie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedury tekstu ogólnego

|Procedura tchar.h|Nie zdefiniowano _UNICODE|_UNICODE zdefiniowano|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Wymagania

|Zmienna globalna|Wymagany nagłówek|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv`i `__wargv` są rozszerzeniami firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)\
[main funkcje i argumenty wiersza poleceniaC++()](../cpp/main-function-command-line-args.md)\
[Używanie wmain zamiast main](../cpp/using-wmain-instead-of-main.md)
