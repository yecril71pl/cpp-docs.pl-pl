---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 31b71f7c195a7e2ee649b40197551e4ff5efda2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584521"
---
# <a name="tlbid"></a>tlbid

**Określonego język C++**

Umożliwia ładowanie bibliotek innych niż biblioteki typu podstawowego.

## <a name="syntax"></a>Składnia

```
tlbid(number)
```

### <a name="parameters"></a>Parametry

*Numer*<br/>
Liczba bibliotekę typów w `filename`.

## <a name="remarks"></a>Uwagi

Jeśli wiele bibliotek typów są wbudowane w pojedynczego pliku DLL, możliwe do załadowania biblioteki inne niż biblioteki typu podstawowego, za pomocą **tlbid**.

Na przykład:

```cpp
#import <MyResource.dll> tlbid(2)
```

jest równoważne:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)