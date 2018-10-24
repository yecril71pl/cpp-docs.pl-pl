---
title: Typy danych OpenMP | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 254dffebc258867088f738b10a11bf48d31bd0a4
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990072"
---
# <a name="openmp-data-types"></a>Typy danych OpenMP

Zawiera łącza do typów danych używanych w interfejsie API OpenMP.

Implementacja języka Visual C++ OpenMP standardowa obejmuje następujące typy danych.

Typ danych                           | Opis
----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[omp_lock_t](#omp-lock-t)           | Typ, który zawiera stan blokady, czy blokada jest dostępny lub jeśli wątek jest właścicielem blokady.
[omp_nest_lock_t](#omp-nest-lock-t) | Typ, który zawiera jedną z następujących rodzajów informacji na temat blokady: czy blokada jest dostępny i tożsamość wątku, który jest właścicielem blokady i liczba zagnieżdżenia.

## <a name="omp-lock-t"></a>omp_lock_t

Typ, który zawiera stan blokady, czy blokada jest dostępny lub jeśli wątek jest właścicielem blokady.

Następujące funkcje użyj `omp_lock_t`:

- [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)
- [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)
- [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)
- [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)
- [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)

Aby uzyskać więcej informacji, zobacz [3.2 funkcje blokady wielowątkowości](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [funkcje omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md) na przykład za pomocą `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

Typ, który zawiera następujące elementy informacji na temat blokady: czy blokada jest dostępny i tożsamość wątku, który jest właścicielem blokady i liczba zagnieżdżenia.

Następujące funkcje użyj `omp_nest_lock_t`:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)
- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)
- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)
- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)
- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

Aby uzyskać więcej informacji, zobacz [3.2 funkcje blokady wielowątkowości](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md) na przykład za pomocą `omp_nest_lock_t`.
