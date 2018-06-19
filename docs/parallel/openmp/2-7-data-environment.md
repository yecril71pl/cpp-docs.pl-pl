---
title: 2.7 środowisko danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 74e44b3c-e18c-4773-8e78-cd6c4413ae57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d1b0f253ce14ffc5d3740e582a9a51feea56ad32
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690068"
---
# <a name="27-data-environment"></a>2.7 Środowisko danych
W tej sekcji przedstawiono dyrektywy i kilka klauzul kontroli środowiska danych podczas wykonywania równoległego regionów, w następujący sposób:  
  
-   A **threadprivate** — dyrektywa (zobacz sekcję poniżej) jest dostępne, aby zakres pliku, zakresie przestrzeni nazw lub zakresem statycznych bloku zmiennych lokalnych do wątku.  
  
-   Klauzule określonych na dyrektywy do kontroli udostępniania atrybutów zmienne w czasie trwania konstrukcji równoległe lub podziału pracy zostały opisane w [sekcji 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) na stronie 25.