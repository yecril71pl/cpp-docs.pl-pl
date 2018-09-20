---
title: 4. Zmienne środowiskowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aec56dad334dcd27de2068e660ff8ec5a6e72f90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415499"
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