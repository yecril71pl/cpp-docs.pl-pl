---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: ae79ce9245bb1c0425c3e9b92dd27b52fa443dba
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
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

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)