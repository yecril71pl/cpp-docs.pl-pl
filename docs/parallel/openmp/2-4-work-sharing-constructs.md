---
title: 2.4 konstrukcje podziału pracy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c00eb94055f26954a283a6172f69228804832ac4
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689639"
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukcje podziału pracy
Konstrukcji podziału pracy dystrybuuje wykonywania skojarzona instrukcja wśród członków zespołu napotykane go. Dyrektywy podziału pracy nie będą uruchamiane wątki nowe, i nie ma żadnych domniemanych bariery wejścia konstrukcji podziału pracy na.  
  
 Konstrukcje podziału pracy sekwencji i **bariery** dyrektywy napotkano musi być taka sama dla każdego wątku w zespole.  
  
 OpenMP — definiuje następujące konstrukcje podziału pracy, a te ustawienia zostały opisane w kolejnych sekcjach:  
  
-   **Aby uzyskać** — dyrektywa  
  
-   **sekcje** — dyrektywa  
  
-   **pojedynczy** — dyrektywa