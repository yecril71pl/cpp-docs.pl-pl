---
title: udostępnione (OpenMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Shared
dev_langs:
- C++
helpviewer_keywords:
- shared OpenMP clause
ms.assetid: 7887dc95-67a2-462f-a3a2-8e0632bf5d04
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 118fa1eb75e8b943b6b490c158e5e21522d57e6c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46441333"
---
# <a name="shared-openmp"></a>udostępnione (OpenMP)

Określa, czy co najmniej jednej zmiennej powinien być współużytkowane przez wszystkie wątki.

## <a name="syntax"></a>Składnia

```
shared(var)
```

### <a name="parameters"></a>Parametry

*var*<br/>
Co najmniej jednej zmiennej do udostępniania. Jeżeli określono więcej niż jedną zmienną, oddziel przecinkami nazw zmiennych.

## <a name="remarks"></a>Uwagi

Innym sposobem udostępnienia zmienne wśród wątków jest [copyprivate](../../../parallel/openmp/reference/copyprivate.md) klauzuli.

`shared` mają zastosowanie do następujących dyrektywach:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)

Aby uzyskać więcej informacji, zobacz [2.7.2.4 udostępnione](../../../parallel/openmp/2-7-2-4-shared.md).

## <a name="example"></a>Przykład

Zobacz [prywatnej](../../../parallel/openmp/reference/private-openmp.md) na przykład za pomocą `shared`.

## <a name="see-also"></a>Zobacz też

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)