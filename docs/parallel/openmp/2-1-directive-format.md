---
title: 2.1 Format dyrektywy
ms.date: 11/04/2016
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
ms.openlocfilehash: 6ee977005d421a59e71f852be3d78a2caad9b45b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629492"
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