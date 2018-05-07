---
title: Uzyskiwanie dostępu do pliku stanu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d424502e991ea355a6e31bba8fedccb6d5ad2fcf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="accessing-file-status"></a>Uzyskiwanie dostępu do stanu pliku
`CFile` również obsługuje pobierania stanu pliku, w tym, czy plik istnieje, tworzenia i modyfikacji daty i godziny, rozmiar logiczny i ścieżki.  
  
### <a name="to-get-file-status"></a>Aby uzyskać stan pliku  
  
1.  Użyj [cfile —](../mfc/reference/cfile-class.md) klasy do pobierania i ustawiania informacji o pliku. Jeden przydatne aplikacji jest użycie `CFile` statycznej funkcji członkowskiej **GetStatus** do ustalenia, czy plik istnieje. **GetStatus** zwraca wartość 0, jeśli określony plik nie istnieje.  
  
 W związku z tym można użyć wyniku **GetStatus** do ustalenia, czy należy użyć **CFile::modeCreate** Flaga podczas otwierania pliku, jak pokazano na poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]  
  
 Aby uzyskać odpowiednie informacje, zobacz [szeregowanie](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Pliki](../mfc/files-in-mfc.md)

