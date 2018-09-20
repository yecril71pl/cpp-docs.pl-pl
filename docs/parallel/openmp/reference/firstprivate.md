---
title: firstprivate | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- firstprivate
dev_langs:
- C++
helpviewer_keywords:
- firstprivate OpenMP clause
ms.assetid: db479766-6d3b-4bbd-b28e-b192d826788c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d070b8de3cf0382447c3b8e756140892dcd85edc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387123"
---
# <a name="firstprivate"></a>firstprivate

Określa, że każdy wątek ma własne wystąpienie zmiennej i że zmiennej powinna zostać zainicjowana z wartością zmiennej, ponieważ istnieje przed konstrukcja równoległa.

## <a name="syntax"></a>Składnia

```
firstprivate(var)
```

#### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`var`|Zmiennej, aby mieć wystąpienia w każdy wątek, który zostanie zainicjowane z wartości zmiennej, ponieważ istnieje przed konstrukcja równoległa. Jeżeli określono więcej niż jedną zmienną, oddziel przecinkami nazw zmiennych.|

## <a name="remarks"></a>Uwagi

## <a name="remarks"></a>Uwagi

`firstprivate` mają zastosowanie do następujących dyrektywach:

- [for](../../../parallel/openmp/reference/for-openmp.md)

- [parallel](../../../parallel/openmp/reference/parallel.md)

- [Sekcje](../../../parallel/openmp/reference/sections-openmp.md)

- [single](../../../parallel/openmp/reference/single.md)

Aby uzyskać więcej informacji, zobacz [2.7.2.2 firstprivate](../../../parallel/openmp/2-7-2-2-firstprivate.md).

## <a name="example"></a>Przykład

Na przykład za pomocą `firstprivate`, zobacz przykład w [prywatnej](../../../parallel/openmp/reference/private-openmp.md).

## <a name="see-also"></a>Zobacz też

[Klauzule](../../../parallel/openmp/reference/openmp-clauses.md)