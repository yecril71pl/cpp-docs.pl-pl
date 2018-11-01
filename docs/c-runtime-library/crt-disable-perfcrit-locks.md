---
title: _CRT_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: 475cc57b5b47f5abf8c268db3acf9e727ce6a743
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593470"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

Wyłącza blokowanie newralgicznym dla wydajności w przypadku operacji We/Wy.

## <a name="syntax"></a>Składnia

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Uwagi

Definiowanie tego symbolu może poprawić wydajność w jednowątkowym I/O-programy, wymuszając wszystkie operacje We/Wy założenie modelu jednowątkowe operacji We/Wy. Aby uzyskać więcej informacji, zobacz [wydajność bibliotek wielowątkowych](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Zobacz też

[Stałe globalne](../c-runtime-library/global-constants.md)