---
title: Uzyskiwanie dostępu do stanu pliku
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 26c263b2d7e4e0243444925cb9416cb337dcd79d
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57298896"
---
# <a name="accessing-file-status"></a>Uzyskiwanie dostępu do stanu pliku

`CFile` również obsługuje pobieranie stanu pliku, w tym, czy plik istnieje, tworzenie i modyfikowanie daty i godziny, rozmiar logiczny i ścieżki.

### <a name="to-get-file-status"></a>Aby uzyskać stan pliku

1. Użyj [CFile](../mfc/reference/cfile-class.md) klasy do pobierania i ustawiania informacji o pliku. Jedna aplikacja przydatne jest użycie `CFile` funkcja statycznej składowej **GetStatus** do ustalenia, czy plik istnieje. **GetStatus** zwraca wartość 0, jeśli określony plik nie istnieje.

W związku z tym, można użyć wyniku **GetStatus** do ustalenia, czy należy użyć **CFile::modeCreate** Flaga podczas otwierania pliku, jak pokazano na poniższym przykładzie:

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Aby uzyskać powiązane informacje, zobacz [serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Pliki](../mfc/files-in-mfc.md)
