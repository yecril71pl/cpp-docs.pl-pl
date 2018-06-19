---
title: Alokowanie i Dealokowanie pamięci okna | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a1364b4d29e2ccd2c9563359716eba6880df5436
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341462"
---
# <a name="allocating-and-deallocating-window-memory"></a>Alokowanie i dealokowanie pamięci okna
Nie należy używać języka C++ **usunąć** operatora, aby zniszczyć okno ramowe lub widoku. Zamiast tego wywołać `CWnd` funkcji członkowskiej `DestroyWindow`. Okna ramowe w związku z tym powinien być przydzielony na stosie z operatorem **nowe**. Należy zachować ostrożność podczas przydzielania okien ramowych w ramce stosu lub globalnie. Powinna zostać przydzielona inne okna w ramce stosu, jeśli to możliwe.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien](../mfc/creating-windows.md)  
  
-   [Sekwencja likwidacji okna](../mfc/window-destruction-sequence.md)  
  
-   [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

