---
title: "Uzyskiwanie dostępu do pliku stanu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9ff93028c192a735ec75721d3dfdb9929a35edad
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-file-status"></a>Uzyskiwanie dostępu do stanu pliku
`CFile`również obsługuje pobierania stanu pliku, w tym, czy plik istnieje, tworzenia i modyfikacji daty i godziny, rozmiar logiczny i ścieżki.  
  
### <a name="to-get-file-status"></a>Aby uzyskać stan pliku  
  
1.  Użyj [cfile —](../mfc/reference/cfile-class.md) klasy do pobierania i ustawiania informacji o pliku. Jeden przydatne aplikacji jest użycie `CFile` statycznej funkcji członkowskiej **GetStatus** do ustalenia, czy plik istnieje. **GetStatus** zwraca wartość 0, jeśli określony plik nie istnieje.  
  
 W związku z tym można użyć wyniku **GetStatus** do ustalenia, czy należy użyć **CFile::modeCreate** Flaga podczas otwierania pliku, jak pokazano na poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 Aby uzyskać odpowiednie informacje, zobacz [szeregowanie](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

