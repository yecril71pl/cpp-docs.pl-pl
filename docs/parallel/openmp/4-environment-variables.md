---
title: 4. Zmienne środowiskowe
ms.date: 11/04/2016
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 0dec302762ad22fc3c7f6691ef63df1b07d5940d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456605"
---
# <a name="4-environment-variables"></a>4. Zmienne środowiskowe

W tym rozdziale opisano zmienne środowiskowe OpenMP C i interfejsu API języka C++ (lub równoważne mechanizmów specyficzne dla platformy), kontrolować wykonywanie kodu przetwarzania równoległego.  Nazwy zmiennych środowiskowych muszą być pisane dużą literą. Wartości przypisane do nich uwzględniana wielkość liter i może mieć początkowe i końcowe biały.  Modyfikacje wartości po uruchomieniu programu są ignorowane.

Zmienne środowiskowe są następujące:

- **OMP_SCHEDULE** ustawia rozmiar typu i fragmentów harmonogramu w czasie wykonywania.

- **OMP_NUM_THREADS** Ustawia liczbę wątków używanych podczas wykonywania.

- **OMP_DYNAMIC** Włącza lub wyłącza dynamiczne Dostosowywanie liczby wątków.

- **OMP_NESTED** Włącza lub wyłącza równoległości zagnieżdżonych.

W przykładach w tym rozdziale jedynie pokazują, jak tych zmiennych może być ustawione w taki sposób, w środowiskach powłoki (csh) C systemu Unix. W Korn powłoki i środowisk systemu DOS akcje są podobne, w następujący sposób:

CSH: setenv OMP_SCHEDULE "dynamiczny"

ksh: eksportowanie OMP_SCHEDULE = "dynamic"

DOS: Ustaw OMP_SCHEDULE = "dynamic"