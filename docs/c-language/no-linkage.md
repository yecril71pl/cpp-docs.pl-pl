---
title: "Brak połączenia | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 278325c1ad1b31ce20b6a17034be5e4731f6da78
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="no-linkage"></a>Brak połączenia
Jeśli nie ma deklaracji dla identyfikatora w bloku `extern` Specyfikator klasy magazynowania, identyfikator ma bez powiązania i jest unikatowa dla funkcji.  
  
 Następujące identyfikatory są bez powiązania:  
  
-   Identyfikator uznane za nic innego niż obiekt lub funkcji  
  
-   Identyfikator zadeklarowana jako parametr funkcji  
  
-   Zasięg bloku identyfikator obiektu zadeklarowana bez `extern` Specyfikator klasy magazynu  
  
 Jeśli identyfikator ma bez połączenia, deklarowanie takiej samej nazwie ponownie (w deklarator lub specyfikatora typu), w tym samym poziomie zakresu generuje błąd zmiana definicji symbolu.  
  
## <a name="see-also"></a>Zobacz też  
 [Użycie zewnętrznie w celu określenia powiązania](../cpp/using-extern-to-specify-linkage.md)