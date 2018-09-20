---
title: Uzyskiwanie dostępu do plików stanu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9f7c2d5d76616ed78768b5e133029cf047ed4453
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416821"
---
# <a name="accessing-file-status"></a>Uzyskiwanie dostępu do stanu pliku

`CFile` również obsługuje pobieranie stanu pliku, w tym, czy plik istnieje, tworzenie i modyfikowanie daty i godziny, rozmiar logiczny i ścieżki.

### <a name="to-get-file-status"></a>Aby uzyskać stan pliku

1. Użyj [CFile](../mfc/reference/cfile-class.md) klasy do pobierania i ustawiania informacji o pliku. Jedna aplikacja przydatne jest użycie `CFile` funkcja statycznej składowej **GetStatus** do ustalenia, czy plik istnieje. **GetStatus** zwraca wartość 0, jeśli określony plik nie istnieje.

W związku z tym, można użyć wyniku **GetStatus** do ustalenia, czy należy użyć **CFile::modeCreate** Flaga podczas otwierania pliku, jak pokazano na poniższym przykładzie:

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Aby uzyskać powiązane informacje, zobacz [serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Pliki](../mfc/files-in-mfc.md)

