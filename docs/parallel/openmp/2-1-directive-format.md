---
title: 2.1 Format dyrektywy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b2f2d2f5742dbc4faa1d8386e935c9d4ccc8049
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424654"
---
# <a name="21-directive-format"></a>2.1 Format dyrektywy

Składnia OpenMP — dyrektywa formalnie jest określona przez gramatyki w [dodatku C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)i nieformalnie w następujący sposób:

```
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Każda dyrektywa zaczyna się od **#pragma omp**, aby zmniejszyć ryzyko będących w konflikcie z innymi dyrektywy pragma (-OpenMP lub dostawcy rozszerzeń OpenMP) przy użyciu takich samych nazwach. W pozostałej części dyrektywa jest zgodna z konwencjami standardów C i C++ dla dyrektywy kompilatora. W szczególności biały znak może służyć przed i po nim **#**, i czasami biały mogą być używane do oddzielania słów w dyrektywie. Przetworzone wstępnie tokeny po **#pragma omp** podlegają wymiana makra.

Dyrektywy jest rozróżniana wielkość liter. Kolejność wyświetlania klauzule w dyrektywach nie ma znaczenia. Klauzule na dyrektywy może się powtarzać, zgodnie z potrzebami, zgodnie z ograniczeniami wymienionych w opisie każdej klauzuli. Jeśli *liście zmiennych* pojawia się w klauzuli on muszą określać tylko zmienne. Tylko jeden *nazwa dyrektywy* może być określona dla dyrektywy.  Na przykład następująca dyrektywa jest niedozwolone:

```
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP — dyrektywa ma zastosowanie do co najwyżej jeden poniższymi instrukcję, która musi być strukturalnego bloku.