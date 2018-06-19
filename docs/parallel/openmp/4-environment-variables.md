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
ms.openlocfilehash: edd4f795a3511358d2b95b93e180b9b21b964dd2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691004"
---
# <a name="4-environment-variables"></a>4. Zmienne środowiskowe
W tym rozdziale opisano zmienne środowiskowe Openmpc i C++ interfejsu API (lub odpowiednik specyficznego dla platformy mechanizmów) umożliwiające sterowanie wykonywanie równoległe kodu.  Nazwy zmiennych środowiskowych muszą być pisane wielkimi literami. Przypisanych do nich wartości uwzględniana jest wielkość liter i może mieć wiodące i końcowe biały znak.  Zmiany w wartości po uruchomieniu programu są ignorowane.  
  
 Zmienne środowiskowe są następujące:  
  
-   **OMP_SCHEDULE** ustawia rozmiar typu i fragmentu harmonogramu czasu wykonywania.  
  
-   **OMP_NUM_THREADS** Ustawia liczbę wątków używanych podczas wykonywania.  
  
-   **OMP_DYNAMIC** Włącza lub wyłącza dynamiczne Dostosowywanie to liczba wątków.  
  
-   **OMP_NESTED** Włącza lub wyłącza równoległości zagnieżdżonych.  
  
 Przykłady w tym rozdziale tylko pokazują, jak te zmienne może być ustawiony w środowiskach powłoki (csh) C systemu Unix. W Korn powłoki i środowisk DOS akcje są podobne, w następujący sposób:  
  
 CSH:  
 SETENV — OMP_SCHEDULE "dynamiczny"  
  
 ksh:  
 Eksportuj OMP_SCHEDULE = "dynamic"  
  
 DOS:  
 Ustaw OMP_SCHEDULE = "dynamic"