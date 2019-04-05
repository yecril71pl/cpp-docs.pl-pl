---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037943"
---
# <a name="tlbid"></a>tlbid

**Określonego język C++**

Umożliwia ładowanie bibliotek innych niż biblioteki typu podstawowego.

## <a name="syntax"></a>Składnia

```
tlbid(number)
```

### <a name="parameters"></a>Parametry

*liczba*<br/>
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

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)