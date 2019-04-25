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
ms.openlocfilehash: 2e6cb2e0d781212f3b5e7758554507dfa438a716
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62289705"
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

## <a name="see-also"></a>Zobacz także

[fseek, _fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[Stałe globalne](../c-runtime-library/global-constants.md)
