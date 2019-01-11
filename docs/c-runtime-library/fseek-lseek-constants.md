---
title: fseek, _lseek — Stałe
ms.date: 11/04/2016
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
ms.openlocfilehash: a97495aaa5ab0a79ed71a48a12162bd14fc60131
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220455"
---
# <a name="fseek-lseek-constants"></a>fseek, _lseek — Stałe

## <a name="syntax"></a>Składnia

```
#include <stdio.h>
```

## <a name="remarks"></a>Uwagi

*Pochodzenia* argument określa położenie początkowe i może być jedną z następujących stałych manifestu:

|Stała|Znaczenie|
|--------------|-------------|
|`SEEK_END`|Koniec pliku|
|`SEEK_CUR`|Bieżącą pozycję wskaźnika pliku|
|`SEEK_SET`|Początek pliku|

## <a name="see-also"></a>Zobacz też

[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
