---
title: "Kody zakończenia z NMAKE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bb5548d74544ba4277fa1d901ffa9f0b91b83f2e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="exit-codes-from-nmake"></a>Kody zakończenia z NMAKE
NMAKE zwraca następujący kod zakończenia:  
  
|Kod|Znaczenie|  
|----------|-------------|  
|0|Błąd (prawdopodobnie ostrzeżenie)|  
|1|Niekompletne kompilacji (wystawiony tylko wtedy, gdy zostanie użyty /K)|  
|2|Błąd programu, prawdopodobnie z powodu jednej z następujących czynności:|  
||— Błąd składni w pliku reguł programu make|  
||— Kod błędu lub zakończenia z polecenia|  
||-Przerwania przez użytkownika|  
|4|Błąd — brak pamięci|  
|255|Element docelowy nie jest aktualny (wystawiony tylko wtedy, gdy zostanie użyty/q)|  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchomienie NMAKE](../build/running-nmake.md)