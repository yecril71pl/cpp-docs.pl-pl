---
title: "Cstring — wyjątek oczyszczania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 68fb6f60c46ff5094e1b7a578a47646f42cea79e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cstring-exception-cleanup"></a>Cstring — wyjątek oczyszczania
W poprzednich wersjach MFC, konieczne jest czyszczenie [cstring —](../atl-mfc-shared/reference/cstringt-class.md) obiektów po użyciu. Z MFC w wersji 3.0 lub nowszej czyszczenia jawne nie jest już konieczne.  
  
 W obszarze mechanizm, który używa teraz MFC obsługi wyjątków języka C++ trzeba martwić oczyszczania po wystąpieniu wyjątku. Opis sposobu C++ "cofa" stosu po Wystąpił wyjątek, zobacz [try, catch i instrukcje throw](../cpp/try-throw-and-catch-statements-cpp.md). Nawet jeśli używasz MFC **SPRÓBUJ**/**CATCH** makra zamiast słowa kluczowe języka C++ **spróbuj** i **catch**, MFC używa języka C++ mechanizm wyjątków poniżej, aby nadal nie trzeba jawnie wyczyścić.  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

