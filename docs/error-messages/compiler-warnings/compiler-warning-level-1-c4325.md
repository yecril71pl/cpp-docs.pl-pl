---
title: Ostrzeżenie kompilatora (poziom 1) C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163027"
---
# <a name="compiler-warning-level-1-c4325"></a>Ostrzeżenie kompilatora (poziom 1) C4325

> atrybuty dla sekcji standardowej "*Section*" zostały zignorowane

## <a name="remarks"></a>Uwagi

Nie można zmienić atrybutów sekcji standardowa. Na przykład:

```cpp
#pragma section(".sdata", long)
```

Spowoduje to zastąpienie standardowej sekcji `.sdata`, która używa typu danych **Short** z typem danych **Long** .

Standardowe sekcje, których atrybuty nie mogą ulec zmianie,

- .data

- .sdata

- . BSS

- .sbss

- . Text

- . const

- .sconst

- . RDATA

- .srdata

Dodatkowe sekcje można dodać później.

## <a name="see-also"></a>Zobacz też

[sekcja](../../preprocessor/section.md)
