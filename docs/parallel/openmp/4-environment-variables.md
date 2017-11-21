---
title: "4. Zmienne środowiskowe | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fcd308f21d66535a983e70506fe91afb5c7042f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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