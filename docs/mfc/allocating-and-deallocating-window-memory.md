---
title: "Alokowanie i Dealokowanie pamięci okna | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 294de3c4d4ecdfcb31f6e8c227bd8a3c6764268d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="allocating-and-deallocating-window-memory"></a>Alokowanie i dealokowanie pamięci okna
Nie należy używać języka C++ **usunąć** operatora, aby zniszczyć okno ramowe lub widoku. Zamiast tego wywołać `CWnd` funkcji członkowskiej `DestroyWindow`. Okna ramowe w związku z tym powinien być przydzielony na stosie z operatorem **nowe**. Należy zachować ostrożność podczas przydzielania okien ramowych w ramce stosu lub globalnie. Powinna zostać przydzielona inne okna w ramce stosu, jeśli to możliwe.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien](../mfc/creating-windows.md)  
  
-   [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)  
  
-   [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

