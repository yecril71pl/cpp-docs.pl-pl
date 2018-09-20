---
title: copyin | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- copyin
dev_langs:
- C++
helpviewer_keywords:
- copyin OpenMP clause
ms.assetid: 369efa88-613c-4cb1-9e11-7b9ee08a4b25
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 424bb8eaa41e3bbb0cf697df108adcef116e1b04
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379584"
---
# <a name="copyin"></a>kopiowanie

Umożliwia wątków, aby uzyskiwać dostęp do wartości głównego wątku dla [threadprivate](../../../parallel/openmp/reference/threadprivate.md) zmiennej.

## <a name="syntax"></a>Składnia

```
copyin(var)
```

## <a name="parameters"></a>Parametry

*var*<br/>
`threadprivate` Zmiennej, która będzie inicjowana przy użyciu wartości zmiennej w głównym wątku, zgodnie z jego lokalizacją przed konstrukcja równoległa.

## <a name="remarks"></a>Uwagi

`copyin` mają zastosowanie do następujących dyrektywach:

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)

Aby uzyskać więcej informacji, zobacz [2.7.2.7 copyin](../../../parallel/openmp/2-7-2-7-copyin.md).

## <a name="example"></a>Przykład

Zobacz [threadprivate](../../../parallel/openmp/reference/threadprivate.md) na przykład za pomocą `copyin`.

## <a name="see-also"></a>Zobacz też

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)