---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: ed4950b9e90ef968fcf0c42e4f0a9775c58ea7ec
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59030170"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Określonego język C++**

Pomija Tworzenie inteligentnych wskaźników dla wszystkich interfejsów w bibliotece typów.

## <a name="syntax"></a>Składnia

```
no_smart_pointers
```

## <a name="remarks"></a>Uwagi

Domyślnie, gdy używasz `#import`, Pobierz deklarację inteligentny wskaźnik dla wszystkich interfejsów w bibliotece typów. Te inteligentne wskaźniki są typu [_com_ptr_t — klasa](../cpp/com-ptr-t-class.md).

**KONIEC określonego języka C++**

## <a name="see-also"></a>Zobacz także

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import Directive](../preprocessor/hash-import-directive-cpp.md)