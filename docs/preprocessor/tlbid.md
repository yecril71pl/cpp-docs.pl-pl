---
title: TLBID — atrybut importowania
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 364fb224b0f2769cb0933e71d18ff70768189328
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216535"
---
# <a name="tlbid-import-attribute"></a>TLBID — atrybut importowania

**C++Specjalne**

Umożliwia ładowanie bibliotek poza podstawową biblioteką typów.

## <a name="syntax"></a>Składnia

> **#import** *typ biblioteki DLL* **TLBID (** *Liczba* **)**

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba bibliotek typów w *bibliotece typów*.

## <a name="remarks"></a>Uwagi

Jeśli wiele bibliotek typów jest wbudowanych w jedną bibliotekę DLL, można załadować biblioteki inne niż podstawowe biblioteki typów za pomocą **TLBID**.

Na przykład:

```cpp
#import <MyResource.dll> tlbid(2)
```

jest równoważne:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**ZAKOŃCZENIE C++ określonych**

## <a name="see-also"></a>Zobacz także

[Atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)
