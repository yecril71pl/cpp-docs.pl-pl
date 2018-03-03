---
title: "Cstring — wyjątek oczyszczania | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CString objects, exceptions
- exception handling, cleanup code
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 496fdfe6a609bd4eceae225c2568c915d38aef07
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cstring-exception-cleanup"></a>Cstring — wyjątek oczyszczania
W poprzednich wersjach MFC, konieczne jest czyszczenie [cstring —](../atl-mfc-shared/reference/cstringt-class.md) obiektów po użyciu. Z MFC w wersji 3.0 lub nowszej czyszczenia jawne nie jest już konieczne.  
  
 W obszarze mechanizm, który używa teraz MFC obsługi wyjątków języka C++ trzeba martwić oczyszczania po wystąpieniu wyjątku. Opis sposobu C++ "cofa" stosu po Wystąpił wyjątek, zobacz [try, catch i instrukcje throw](../cpp/try-throw-and-catch-statements-cpp.md). Nawet jeśli używasz MFC **SPRÓBUJ**/**CATCH** makra zamiast słowa kluczowe języka C++ **spróbuj** i **catch**, MFC używa języka C++ mechanizm wyjątków poniżej, aby nadal nie trzeba jawnie wyczyścić.  
  
## <a name="see-also"></a>Zobacz też  
 [Ciągi (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Obsługa wyjątków](../mfc/exception-handling-in-mfc.md)

