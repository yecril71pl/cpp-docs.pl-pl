---
title: __argc __argv, __wargv | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- __wargv
- __argv
- __argc
apilocation:
- msvcrt120.dll
apitype: DLLExport
f1_keywords:
- __argv
- __argc
- __wargv
dev_langs:
- C++
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fada373439f331ffc0db6af0972c77a92d6d5f57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062036"
---
# <a name="argc-argv-wargv"></a>__argc __argv, __wargv

`__argc` Zmienna globalna jest liczbę argumentów wiersza polecenia przekazywane do programu. `__argv` wskaźnik do tablicy ciągi pojedynczych bajtów znaków lub wielu byte znaków, które zawierają argumenty programu i `__wargv` jest wskaźnikiem do tablicy ciągów znaków dwubajtowych, które zawierają argumenty programu. Tych zmiennych globalnych podać argumenty `main` lub `wmain`.

## <a name="syntax"></a>Składnia

```
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Uwagi

W programie, który używa `main` funkcji `__argc` i `__argv` są inicjowane w momencie uruchamiania programu przy użyciu wiersza polecenia, które jest używane do uruchamiania programu. W wierszu polecenia jest przekształcany do pojedynczych argumentów, a zostaną rozwinięte symbole wieloznaczne. Liczba argumentów jest przypisany do `__argc` ciągów argumentów są przydzielane na stosie i wskaźnik do tablicy argumentów jest przypisany do `__argv`. W programie skompilowane do użycia znaków dwubajtowych i `wmain` funkcji, argumenty są parsowane symbole wieloznaczne są rozwijane jako ciągi znaków dwubajtowych i wskaźnika do tablicy ciągów argument jest przypisany do `__wargv`.

Kod przenośny, zaleca się używać argumentów przekazanych do `main` uzyskać argumenty wiersza polecenia w programie.

### <a name="generic-text-routine-mappings"></a>Mapowania procedur zwykłego tekstu

|Procedura tchar.h|_UNICODE niezdefiniowana|_UNICODE zdefiniowano|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>Wymagania

|Zmienna globalna|Wymagany nagłówek|
|---------------------|---------------------|
|`__argc`, `__argv`, `__wargv`|\<stdlib.h>, \<cstdlib> (C++)|

`__argc`, `__argv`, i `__wargv` są rozszerzeniami Microsoft. Aby uzyskać informacje o zgodności – zobacz [zgodności](../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Zobacz też

[Zmienne globalne](../c-runtime-library/global-variables.md)<br/>
[main: uruchamianie programu](../cpp/main-program-startup.md)<br/>
[Korzystanie z wmain zamiast main](../cpp/using-wmain-instead-of-main.md)