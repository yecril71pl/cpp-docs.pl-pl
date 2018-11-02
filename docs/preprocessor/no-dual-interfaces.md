---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: d76fe3ce6bea4c3895da9d8b40d69852f912824e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466732"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Określonego język C++**

Zmienia sposób, kompilator generuje funkcje otoki dla metod podwójnego interfejsu.

## <a name="syntax"></a>Składnia

```
no_dual_interfaces
```

## <a name="remarks"></a>Uwagi

Zwykle otoki wywoła metodę przez tabelę funkcji wirtualnych dla interfejsu. Za pomocą **no_dual_interfaces —**, zamiast tego wywołania otoki `IDispatch::Invoke` było wywołanie metody.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)