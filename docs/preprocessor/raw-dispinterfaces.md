---
title: raw_dispinterfaces
ms.date: 11/04/2016
f1_keywords:
- raw_dispinterfaces
helpviewer_keywords:
- raw_dispinterfaces attribute
ms.assetid: f762864d-29bf-445b-825a-ba7b29a95409
ms.openlocfilehash: 8a6c335c7afe2cc56613f06abf5c181f05f6bfec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585396"
---
# <a name="rawdispinterfaces"></a>raw_dispinterfaces
**Określonego język C++**

Informuje kompilator, aby wygenerować otoki niskiego poziomu funkcji dispinterface metody i właściwości, które wywołują `IDispatch::Invoke` i zwracają kod błędu HRESULT.

## <a name="syntax"></a>Składnia

```
raw_dispinterfaces
```

## <a name="remarks"></a>Uwagi

Jeśli ten atrybut nie jest określony, tylko ogólne są generowane otoki, która generuje wyjątków C++ w przypadku awarii.

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)