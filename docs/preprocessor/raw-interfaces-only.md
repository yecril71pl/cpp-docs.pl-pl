---
title: raw_interfaces_only
ms.date: 11/04/2016
f1_keywords:
- raw_interfaces_only
helpviewer_keywords:
- raw_interfaces_only attribute
ms.assetid: 87056c6d-3f34-4248-af58-f5775a35bfb7
ms.openlocfilehash: c07401036261b9f93bb2c07dcf3aff1ecf72e2fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519356"
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

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)