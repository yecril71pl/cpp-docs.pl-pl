---
title: Stałe uprawnień pliku
ms.date: 11/04/2016
f1_keywords:
- _S_IWRITE
- _S_IREAD
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
ms.openlocfilehash: 0e4a60b5f3dad70f881387d5befca2def9bff7f3
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520429"
---
# <a name="file-permission-constants"></a>Stałe uprawnień pliku

## <a name="syntax"></a>Składnia

```

#include <sys/stat.h>
```

## <a name="remarks"></a>Uwagi

Jedną z tych stałych jest wymagany, gdy `_O_CREAT` (`_open`, `_sopen`) jest określony.

`pmode` Argument określa ustawienia uprawnień pliku w następujący sposób.

|Stała|Znaczenie|
|--------------|-------------|
|`_S_IREAD`|Odczytywanie dozwolone|
|`_S_IWRITE`|Zapisywanie dozwolone|
|`_S_IREAD` &#124; `_S_IWRITE`|Odczytywanie i zapisywanie dozwolone|

Gdy jest używana jako `pmode` argument `_umask`, stała manifestu ustawia ustawienie uprawnienia w następujący sposób.

|Stała|Znaczenie|
|--------------|-------------|
|`_S_IREAD`|Zapisywanie niedozwolone (plik jest tylko do odczytu)|
|`_S_IWRITE`|Odczytywanie niedozwolone (plik jest tylko do zapisu)|
|`_S_IREAD` &#124; `_S_IWRITE`|Zapisywanie ani odczytywanie dozwolone|

## <a name="see-also"></a>Zobacz też

[_open, _wopen](../c-runtime-library/reference/open-wopen.md)<br/>
[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md)<br/>
[_umask](../c-runtime-library/reference/umask.md)<br/>
[Standardowe typy](../c-runtime-library/standard-types.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)