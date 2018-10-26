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
ms.openlocfilehash: 97cf6ccad0a3b30c0abfa0076ea9c6a30b205d67
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065203"
---
# <a name="openmp-data-types"></a>Typy danych OpenMP

Zawiera łącza do typów danych używanych w interfejsie API OpenMP.

Implementacja języka Visual C++ OpenMP standardowa obejmuje następujące typy danych.

|Typ danych|Opis|
|---------|-----------|
|[omp_lock_t](#omp-lock-t)|Typ, który zawiera stan blokady, czy blokada jest dostępny lub jeśli wątek jest właścicielem blokady.|
|[omp_nest_lock_t](#omp-nest-lock-t)|Typ, który zawiera jedną z następujących rodzajów informacji na temat blokady: czy blokada jest dostępny i tożsamość wątku, który jest właścicielem blokady i liczba zagnieżdżenia.|

## <a name="omp-lock-t"></a>omp_lock_t

Typ, który zawiera stan blokady, czy blokada jest dostępny lub jeśli wątek jest właścicielem blokady.

Następujące funkcje użyj `omp_lock_t`:

- [omp_init_lock](openmp-functions.md#omp-init-lock)
- [omp_destroy_lock](openmp-functions.md#omp-destroy-lock)
- [omp_set_lock](openmp-functions.md#omp-set-lock)
- [omp_unset_lock](openmp-functions.md#omp-unset-lock)
- [omp_test_lock](openmp-functions.md#omp-test-lock)

Aby uzyskać więcej informacji, zobacz [3.2 funkcje blokady wielowątkowości](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [funkcje omp_init_lock](openmp-functions.md#omp-init-lock) na przykład za pomocą `omp_lock_t`.

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

Typ, który zawiera następujące elementy informacji na temat blokady: czy blokada jest dostępny i tożsamość wątku, który jest właścicielem blokady i liczba zagnieżdżenia.

Następujące funkcje użyj `omp_nest_lock_t`:

- [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)
- [omp_destroy_nest_lock](openmp-functions.md#omp-destroy-nest-lock)
- [omp_set_nest_lock](openmp-functions.md#omp-set-nest-lock)
- [omp_unset_nest_lock](openmp-functions.md#omp-unset-nest-lock)
- [omp_test_nest_lock](openmp-functions.md#omp-test-nest-lock)

Aby uzyskać więcej informacji, zobacz [3.2 funkcje blokady wielowątkowości](../../../parallel/openmp/3-2-lock-functions.md).

### <a name="example"></a>Przykład

Zobacz [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock) na przykład za pomocą `omp_nest_lock_t`.
