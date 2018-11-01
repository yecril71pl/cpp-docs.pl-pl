---
title: Stałe dostępu do odczytu i zapisu pliku
ms.date: 11/04/2016
f1_keywords:
- c.constants.file
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
ms.openlocfilehash: 7bf16271c0d58e3d87e4c24795ec0bd1ee1ccb89
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666192"
---
# <a name="file-readwrite-access-constants"></a>Odczyt/zapis pliku — Stałe dostępu

## <a name="syntax"></a>Składnia

```
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

Te stałe Określ typ dostępu ("a", "r" lub "t"), wnioskowany dla pliku. Zarówno [tryb translacji](../c-runtime-library/file-translation-constants.md) ("b" lub "t") i [tryb commit-to-disk](../c-runtime-library/commit-to-disk-constants.md) ("c" lub "n") można określić za pomocą typu dostępu.

W tej tabeli opisano typy dostępu:

|Typ dostępu|Opis|
|----------|----------------|
|**"r"**|Otwiera do odczytu. Jeśli plik nie istnieje lub nie można znaleźć, wywołanie do otwierania pliku kończy się niepowodzeniem.|
|**"w"**|Otwiera pusty plik do zapisu. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**""**|Zostanie otwarty do zapisu na końcu pliku (dołączanie); najpierw tworzy plik, jeśli nie istnieje. Zapisu wszystkie operacje są wykonywane na końcu pliku. Mimo że wskaźnik pliku może być przeniesiony za pomocą `fseek` lub `rewind`, on jest zawsze przenoszony z powrotem na koniec pliku przed wszelkie zapisu operacji jest przeprowadzane. |
|**"r +"**|Otwiera Odczyt i zapis. Jeśli plik nie istnieje lub nie można znaleźć, wywołanie do otwierania pliku kończy się niepowodzeniem.|
|**"w +"**|Otwiera pusty plik Odczyt i zapis. Jeśli dany plik istnieje, jego zawartość zostaje zniszczona.|
|**"+"**|Taka sama jak **""** , ale również umożliwia odczyt.|

Jeśli "r +", "w +" lub "+" typ jest określony, będą miały Odczyt i zapis (plik jest określany jako otwarty do "aktualizacji"). Jednak podczas przełączania się między Odczyt i zapis, musi istnieć interwencyjne `fflush`, `fsetpos`, `fseek`, lub `rewind` operacji. Bieżąca pozycja może być określona dla `fsetpos` lub `fseek` operacji.

## <a name="see-also"></a>Zobacz też

[_fdopen, _wfdopen](../c-runtime-library/reference/fdopen-wfdopen.md)<br/>
[fopen, _wfopen](../c-runtime-library/reference/fopen-wfopen.md)<br/>
[freopen, _wfreopen](../c-runtime-library/reference/freopen-wfreopen.md)<br/>
[_fsopen, _wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md)<br/>
[_popen, _wpopen](../c-runtime-library/reference/popen-wpopen.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)