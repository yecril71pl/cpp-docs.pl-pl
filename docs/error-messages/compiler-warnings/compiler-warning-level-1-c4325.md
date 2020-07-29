---
title: Ostrzeżenie kompilatora (poziom 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 551680bc1d24097200a1e641bc4238f883ad94dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230704"
---
# <a name="compiler-warning-level-1-c4325"></a>Ostrzeżenie kompilatora (poziom 1) C4325

> atrybuty dla sekcji standardowej "*Section*" zostały zignorowane

## <a name="remarks"></a>Uwagi

Nie można zmienić atrybutów sekcji standardowa. Na przykład:

```cpp
#pragma section(".sdata", long)
```

Spowoduje to zastąpienie `.sdata` standardowej sekcji, która używa **`short`** typu danych z **`long`** typem danych.

Standardowe sekcje, których atrybuty nie mogą ulec zmianie,

- . dane

- . sdata

- . BSS

- . sbss

- . Text

- . const

- .sconst

- . RDATA

- .srdata

Dodatkowe sekcje można dodać później.

## <a name="see-also"></a>Zobacz także

[Paragraf](../../preprocessor/section.md)
