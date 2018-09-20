---
title: domyślne (OpenMP) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- default
dev_langs:
- C++
helpviewer_keywords:
- default OpenMP clause
- defaults, OpenMP clause
ms.assetid: 96055106-a8f0-40b3-8319-e412b6e07bf8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4ea32f473d96c8f48c6628d8f71212269bd6d345
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392618"
---
# <a name="default-openmp"></a>domyślne (OpenMP)

Określa zachowanie zmiennych niewystępującego w zakresie równoległego regionu.

## <a name="syntax"></a>Składnia

```
default(shared | none)
```

## <a name="remarks"></a>Uwagi

`shared`, która obowiązuje Jeśli `default` klauzula nie jest określony, oznacza, że dowolnej zmiennej w równoległego regionu będą traktowane tak, jakby zostały określone z [udostępnionego](../../../parallel/openmp/reference/shared-openmp.md) klauzuli. `none` oznacza, że wszystkie zmienne używane w regionie równoległych, które nie są w zakresie z [prywatnej](../../../parallel/openmp/reference/private-openmp.md), [udostępnionego](../../../parallel/openmp/reference/shared-openmp.md), [redukcji](../../../parallel/openmp/reference/reduction.md), [firstprivate](../../../parallel/openmp/reference/firstprivate.md), lub [lastprivate](../../../parallel/openmp/reference/lastprivate.md) klauzuli spowoduje błąd kompilatora.

`default` mają zastosowanie do następujących dyrektywach:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)

Aby uzyskać więcej informacji, zobacz [2.7.2.5 domyślne](../../../parallel/openmp/2-7-2-5-default.md).

## <a name="example"></a>Przykład

Zobacz [prywatnej](../../../parallel/openmp/reference/private-openmp.md) na przykład za pomocą `default`.

## <a name="see-also"></a>Zobacz też

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)