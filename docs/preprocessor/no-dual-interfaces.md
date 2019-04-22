---
title: no_dual_interfaces
ms.date: 11/04/2016
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: ae75bc2e974f374768f1a9e5a0e1ced61e9904b0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59023805"
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

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)