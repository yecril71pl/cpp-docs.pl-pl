---
title: Kody zakończenia z NMAKE | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, exit codes
- exit codes
ms.assetid: 75f6913c-1da5-4572-a2d3-8a4e058bed15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4e71442e1e36dbd69afa65051cbf08f403bf8b31
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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