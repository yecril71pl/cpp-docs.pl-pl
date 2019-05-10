---
title: Kontener Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: b344747c42e9b8b751b97747aacec0b39d10d6a1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221518"
---
# <a name="container-classswap"></a>Kontener Class::swap

> [!NOTE]
> W tym temacie znajduje się w Microsoft C++ przesłać dokumenty będące prawidłowo przykład kontenerów używanych w C++ biblioteki standardowej. Aby uzyskać więcej informacji, zobacz [standardowych kontenerów biblioteki języka C++](../standard-library/stl-containers.md).

Zamienia kontrolowanej sekwencji między  **\*to** i jej argument.

## <a name="syntax"></a>Składnia

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Uwagi

Jeśli  **\*this.get\_alokatora ==** _prawo_**.get_allocator**, robi zamiany w stałym czasie. W przeciwnym razie wykonuje szereg element zadania i Konstruktor wywołuje proporcjonalna do liczby elementów w dwóch kontrolowanej sekwencji.

## <a name="see-also"></a>Zobacz także

[Sample Container, klasa](../standard-library/sample-container-class.md)<br/>
