---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: 48133b85ccb5ddb8de8e6cb614d41cde22dac66b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028263"
---
# <a name="rawinterfacesonly"></a>raw_interfaces_only
**Określonego język C++**

Pomija generację funkcje otoki obsługi błędów i [właściwość](../cpp/property-cpp.md) deklaracji, korzystających z tych funkcji otoki.

## <a name="syntax"></a>Składnia

```
raw_interfaces_only
```

## <a name="remarks"></a>Uwagi

**Raw_interfaces_only —** atrybut również powoduje, że domyślny prefiks używany w nazwach funkcji inną niż właściwość, które mają zostać usunięte. Zazwyczaj jest prefiks **raw_**. Jeśli ten atrybut jest określony, nazwy funkcji są bezpośrednio z biblioteki typów.

Ten atrybut umożliwia uwidocznienie niskiego poziomu zawartość biblioteki typów.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)