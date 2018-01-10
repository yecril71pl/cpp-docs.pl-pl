---
title: "Odczytywanie zakresów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 99de29ce-ab14-46f4-97e1-2081fd996b53
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 36fd3354e21b063dba05e24e1e3ba0d206a89343
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="reading-ranges"></a>Odczytywanie zakresów
**ANSI 4.9.6.2** interpretacji znak kreski (-), który jest ani pierwszym ani ostatnim znakiem w scanlist % [konwersja w `fscanf` — funkcja  
  
 Następujący wiersz  
  
```  
fscanf( fileptr, "%[A-Z]", strptr);  
```  
  
 odczytuje dowolną liczbę znaków z zakresu A-Z w ciągu do której `strptr` punktów.  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje bibliotek](../c-language/library-functions.md)