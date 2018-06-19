---
title: Zamykanie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, file operations
- files [MFC], closing
ms.assetid: 8415a3a8-3c75-45b0-ac2a-d5385f49bdb3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 97bd910ae4cb514cda07dd319f37a05a32712909
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341029"
---
# <a name="closing-files"></a>Zamykanie plików
Normalnie w operacji We/Wy, po zakończeniu pracy z pliku, należy go zamknąć.  
  
#### <a name="to-close-a-file"></a>Aby zamknąć plik  
  
1.  Użyj **Zamknij** funkcję elementu członkowskiego. Ta funkcja powoduje zamknięcie pliku system plików i opróżnienia buforów, jeśli to konieczne.  
  
 Jeśli została przydzielona [cfile —](../mfc/reference/cfile-class.md) obiektu w ramce (tak jak pokazano w przykładzie [otwieranie plików](../mfc/opening-files.md)), obiekt zostanie automatycznie zamknięte, a następnie niszczony, kiedy przechodzi ona poza zakresem. Należy pamiętać, że usunięcie `CFile` obiektu nie powoduje usunięcia pliku fizycznego w systemie plików.  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

