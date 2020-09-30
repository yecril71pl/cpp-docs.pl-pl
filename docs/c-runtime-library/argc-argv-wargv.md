---
title: __argc, __argv, __wargv
description: Opisuje globalne stałe biblioteki środowiska uruchomieniowego Microsoft C __argc , __argv i __wargv .
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
ms.openlocfilehash: 02c130be0d2dcb8e48d2bb5c75438c94003fc9dd
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507594"
---
# <a name="no-loc__argc-no-loc__argv-no-loc__wargv"></a>__argc, __argv, __wargv

`__argc`Zmienna globalna jest liczbą argumentów wiersza polecenia przekazaną do programu. `__argv` jest wskaźnikiem do tablicy ciągów o pojedynczym bajcie lub wielobajtowym znakiem, które zawierają argumenty programu, i `__wargv` jest wskaźnikiem do tablicy ciągów o szerokim znaku, które zawierają argumenty programu. Te zmienne globalne zapewniają argumenty do `main` lub `wmain` .

## <a name="syntax"></a>Składnia

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Uwagi

W programie, który korzysta z `main` funkcji  `__argc` i `__argv` są inicjowane przy uruchamianiu programu przy użyciu wiersza polecenia, który służy do uruchamiania programu. Wiersz polecenia jest analizowany w poszczególnych argumentach, a symbole wieloznaczne są rozwinięte. Liczba argumentów jest przypisana do `__argc` i ciągi argumentów są przydzielane na stercie, a wskaźnik do tablicy argumentów jest przypisany do `__argv` . W programie skompilowanym do używania znaków dwubajtowych i `wmain` funkcji, argumenty są analizowane, a symbole wieloznaczne są rozwinięte jako ciągi o szerokim znaku, a wskaźnik do tablicy ciągów argumentów jest przypisany do `__wargv` .

W przypadku kodu przenośnego zalecamy używanie argumentów przekazane do w `main` celu uzyskania argumentów wiersza polecenia w programie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedury tekstu ogólnego

|Procedura tchar.h|Nie zdefiniowano _UNICODE|_UNICODE zdefiniowano|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Wymagania

|Zmienna globalna|Wymagany nagłówek|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv` i `__wargv` są rozszerzeniami firmy Microsoft. Aby uzyskać informacje o zgodności, zobacz [zgodność](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Zmienne globalne](../c-runtime-library/global-variables.md)\
[main argumenty funkcji i wiersza polecenia (C++)](../cpp/main-function-command-line-args.md)\
[Używanie wmain zamiast main](../cpp/main-function-command-line-args.md)
