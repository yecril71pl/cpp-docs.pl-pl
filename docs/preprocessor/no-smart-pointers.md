---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 305c08497a600f602767496cba48d108335fdeb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636985"
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

## <a name="see-also"></a>Zobacz też

[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)