---
title: __argc, __argv, __wargv
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
ms.openlocfilehash: 59ab1f5ba52e6dc84d44e8cb5465cfa412d01895
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940634"
---
# <a name="__argc-__argv-__wargv"></a>__argc, __argv, __wargv

Zmienna `__argc` globalna jest liczbą argumentów wiersza polecenia przekazaną do programu. `__argv`jest wskaźnikiem do tablicy ciągów o pojedynczym bajcie lub wielobajtowym znakiem, które zawierają argumenty programu, i `__wargv` jest wskaźnikiem do tablicy ciągów o szerokim znaku, które zawierają argumenty programu. Te zmienne globalne zapewniają argumenty do `main` lub. `wmain`

## <a name="syntax"></a>Składnia

```
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Uwagi

W programie, `__argc` który korzysta z `main` funkcji i `__argv` są inicjowane przy uruchamianiu programu przy użyciu wiersza polecenia, który służy do uruchamiania programu. Wiersz polecenia jest analizowany w poszczególnych argumentach, a symbole wieloznaczne są rozwinięte. Liczba argumentów jest przypisana do `__argc` i ciągi argumentów są przydzielane na stercie, a wskaźnik do tablicy argumentów jest przypisany do. `__argv` W programie skompilowanym do używania znaków dwubajtowych `wmain` i funkcji, argumenty są analizowane, a symbole wieloznaczne są rozwinięte jako ciągi o szerokim znaku, a wskaźnik do tablicy ciągów argumentów jest przypisany do `__wargv`.

W przypadku kodu przenośnego zalecamy używanie argumentów przekazane do `main` w celu uzyskania argumentów wiersza polecenia w programie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|Nie zdefiniowano _UNICODE|_UNICODE zdefiniowano|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Wymagania

|Zmienna globalna|Wymagany nagłówek|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv` i`__wargv` są rozszerzeniami firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz także

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[main: uruchamianie programu](../cpp/main-program-startup.md)<br/>
[Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)
