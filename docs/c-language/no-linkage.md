---
title: Brak połączenia | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- no linkage
- linkage [C++], none
ms.assetid: 5a413082-1034-4e04-b76b-8d14668bf434
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc6515020272d19a9b9efca7341293be4983a56
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32383790"
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