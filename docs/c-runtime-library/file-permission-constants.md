---
title: Stałe uprawnień pliku
ms.date: 11/04/2016
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 9f6126b867e29ca37468c6ff383224a483639c78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443276"
---
# <a name="file-permission-constants"></a>Stałe uprawnień pliku

## <a name="syntax"></a>Składnia

```
#include <sys/stat.h>
```

## <a name="remarks"></a>Uwagi

Jedna z tych stałych jest wymagana w przypadku określenia `_O_CREAT` (`_open`, `_sopen`).

`pmode` argument określa ustawienia uprawnień pliku w następujący sposób.

|Stały|Znaczenie|
|--------------|-------------|
|`_S_IREAD`|Odczytywanie dozwolone|
|`_S_IWRITE`|Dozwolone zapisywanie|
|`_S_IREAD` &#124; `_S_IWRITE`|Dozwolone odczytywanie i zapisywanie|

W przypadku użycia jako argumentu `pmode` dla `_umask`, stała manifestu ustawia ustawienie uprawnień w następujący sposób.

|Stały|Znaczenie|
|--------------|-------------|
|`_S_IREAD`|Zapisywanie nie jest dozwolone (plik jest tylko do odczytu)|
|`_S_IWRITE`|Odczytywanie jest niedozwolone (plik jest tylko do zapisu)|
|`_S_IREAD` &#124; `_S_IWRITE`|Nie ma uprawnień do odczytu ani zapisu|

## <a name="see-also"></a>Zobacz też

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Standardowe typy](../c-runtime-library/standard-types.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
