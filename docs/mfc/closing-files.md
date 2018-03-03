---
title: "Zamykanie plików | Dokumentacja firmy Microsoft"
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
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 27b1c59c952b022c7382db7d6b2dcb660cca2e9a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="closing-files"></a>Zamykanie plików
Normalnie w operacji We/Wy, po zakończeniu pracy z pliku, należy go zamknąć.  
  
#### <a name="to-close-a-file"></a>Aby zamknąć plik  
  
1.  Użyj **Zamknij** funkcję elementu członkowskiego. Ta funkcja powoduje zamknięcie pliku system plików i opróżnienia buforów, jeśli to konieczne.  
  
 Jeśli została przydzielona [cfile —](../mfc/reference/cfile-class.md) obiektu w ramce (tak jak pokazano w przykładzie [otwieranie plików](../mfc/opening-files.md)), obiekt zostanie automatycznie zamknięte, a następnie niszczony, kiedy przechodzi ona poza zakresem. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

