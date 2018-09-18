---
title: Stałe uprawnień pliku | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _S_IWRITE
- _S_IREAD
dev_langs:
- C++
helpviewer_keywords:
- S_IWRITE constant
- constants [C++], file attributes
- S_IREAD constant
- file permissions [C++]
- _S_IWRITE constant
- _S_IREAD constant
ms.assetid: 593cad33-31d1-44d2-8941-8af7d210c88c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ae2e7d669edda1ab3069cf3cdb30b79482047e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026647"
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