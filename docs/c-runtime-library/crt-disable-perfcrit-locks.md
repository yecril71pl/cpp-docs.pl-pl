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
ms.openlocfilehash: b6f4d8dee5577e88aa59af9bff017aab0c7eef89
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344601"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

Wyłącza blokowanie newralgicznym dla wydajności w przypadku operacji We/Wy.

## <a name="syntax"></a>Składnia

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>Uwagi

Definiowanie tego symbolu może poprawić wydajność w jednowątkowym I/O-programy, wymuszając wszystkie operacje We/Wy założenie modelu jednowątkowe operacji We/Wy. Aby uzyskać więcej informacji, zobacz [wydajność bibliotek wielowątkowych](../c-runtime-library/multithreaded-libraries-performance.md).

## <a name="see-also"></a>Zobacz także

[Stałe globalne](../c-runtime-library/global-constants.md)
