---
title: "Zalety i wady i zalety metody używanej do łącza do CRT | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- _ATL_MIN_CRT macro
ms.assetid: 49b485f7-9487-49e4-b12a-0f710b620e2b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 244415a947918a836e8c4c67dbd18758ec40393c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="benefits-and-tradeoffs-of-the-method-used-to-link-to-the-crt"></a>Zalety i wady i zalety metody używanej do łącza do CRT
Projekt można połączyć z CRT dynamicznie lub statycznie. W poniższej tabeli przedstawiono zalety i wady i zalety objętego wybranie metody.  
  
|Metoda|Korzyść|Zależnościami|  
|------------|-------------|--------------|  
|Statycznie łączenia CRT<br /><br /> (**Biblioteki wykonawczej** ustawioną **jednowątkowe**)|Biblioteki DLL CRT nie jest wymagane w systemie, gdy obraz zostanie uruchomiony.|Około 25K uruchamiania kodu jest dodawany do obrazu systemu znaczne zwiększenie jego rozmiaru.|  
|Dynamicznie łączenie z CRT<br /><br /> (**Biblioteki wykonawczej** ustawioną **wielowątkowych**)|Obraz nie wymaga kod uruchomienia CRT, dlatego jest znacznie mniejszy.|Biblioteki DLL CRT musi być obraz systemu.|  
  
 Temat [łączenia CRT w swój projekt ATL](../atl/linking-to-the-crt-in-your-atl-project.md) omówiono sposób Wybierz sposób, w którym do odesłania do CRT.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie za pomocą ALT i C Run-Time kodu](../atl/programming-with-atl-and-c-run-time-code.md)   
 [Biblioteki dll i zachowanie biblioteki wykonawczej programu Visual C++](../build/run-time-library-behavior.md)   
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)

