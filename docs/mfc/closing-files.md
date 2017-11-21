---
title: "Zamykanie plików | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3833763394eda3ad64f1c72b80bee4d76785d5a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="closing-files"></a>Zamykanie plików
Normalnie w operacji We/Wy, po zakończeniu pracy z pliku, należy go zamknąć.  
  
#### <a name="to-close-a-file"></a>Aby zamknąć plik  
  
1.  Użyj **Zamknij** funkcję elementu członkowskiego. Ta funkcja powoduje zamknięcie pliku system plików i opróżnienia buforów, jeśli to konieczne.  
  
 Jeśli została przydzielona [cfile —](../mfc/reference/cfile-class.md) obiektu w ramce (tak jak pokazano w przykładzie [otwieranie plików](../mfc/opening-files.md)), obiekt zostanie automatycznie zamknięte, a następnie niszczony, kiedy przechodzi ona poza zakresem. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

