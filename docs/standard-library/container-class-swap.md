---
title: Kontener Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: ccf4ae6ebc3ca13a42ca950310a60e30dbb27034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450770"
---
# <a name="container-classswap"></a>Kontener Class::swap

> [!NOTE]
> Ten temat znajduje się w dokumentacji C++ firmy Microsoft jako przykład niefunkcjonalny kontenerów używanych w C++ standardowej bibliotece. Aby uzyskać więcej informacji, zobacz [ C++ Kontenery biblioteki standardowej](../standard-library/stl-containers.md).

Zamienia kontrolowane sekwencje między  **\*tym** i argumentem.

## <a name="syntax"></a>Składnia

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Uwagi

W  **\*takimprzypadkuprogramprzydzielający==Right.get_allocatorwykonujewymianęwstałym\_** czasie. W przeciwnym razie wykonuje wiele przypisań elementów i wywołań konstruktora proporcjonalnie do liczby elementów w dwóch kontrolowanej sekwencji.

## <a name="see-also"></a>Zobacz także

[Sample Container, klasa](../standard-library/sample-container-class.md)
