---
title: "2.4 konstrukcje podziału pracy | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 476e4e23b22527accaa095d80b827c95aed58c15
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="24-work-sharing-constructs"></a>2.4 Konstrukcje podziału pracy
Konstrukcji podziału pracy dystrybuuje wykonywania skojarzona instrukcja wśród członków zespołu napotykane go. Dyrektywy podziału pracy nie będą uruchamiane wątki nowe, i nie ma żadnych domniemanych bariery wejścia konstrukcji podziału pracy na.  
  
 Konstrukcje podziału pracy sekwencji i **bariery** dyrektywy napotkano musi być taka sama dla każdego wątku w zespole.  
  
 OpenMP — definiuje następujące konstrukcje podziału pracy, a te ustawienia zostały opisane w kolejnych sekcjach:  
  
-   **Aby uzyskać** — dyrektywa  
  
-   **sekcje** — dyrektywa  
  
-   **pojedynczy** — dyrektywa