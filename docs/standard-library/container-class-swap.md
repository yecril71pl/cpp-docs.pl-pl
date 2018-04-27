---
title: Kontener Class::swap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3c6691b8ee8471ebf0e8edc8f1513d0229193a4a
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="container-classswap"></a>Kontener Class::swap

> [!NOTE]
> Ten temat dotyczy w dokumentacji Visual C++ prawidłowo przykład kontenerów używanych w standardowej bibliotece C++. Aby uzyskać więcej informacji, zobacz [standardowe kontenery biblioteki C++](../standard-library/stl-containers.md).

Zamienia kontrolowanej sekwencji między  **\*to** i jej argument.

## <a name="syntax"></a>Składnia

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Uwagi

Jeśli  **\*this.get\_alokatora ==** _prawo_**.get_allocator**, robi zamiana w czasie stałej. W przeciwnym razie wykonuje szereg element zadania i wywołania konstruktora proporcjonalny do liczby elementów w dwóch kontrolowanej sekwencji.

## <a name="see-also"></a>Zobacz także

[Sample Container, klasa](../standard-library/sample-container-class.md)<br/>
