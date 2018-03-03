---
title: "Kody zakończenia z NMAKE | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13cbe4806d8b3960cbf80df41c7cce6e7657ba7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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