---
title: Klasy We / Wy plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.file
dev_langs:
- C++
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fad854b054ca32819597126c5a4c0b9652df9210
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442139"
---
# <a name="file-io-classes"></a>Klasy we/wy plików

Te klasy oferują interfejs do plików na tradycyjnych dysku, plików w pamięci, aktywne strumienie i Windows sockets. Wszystkie klasy pochodne `CFile` mogą być używane z `CArchive` obiektu w celu wykonania serializacji.

Użyj następujących klas, zwłaszcza `CArchive` i `CFile`, jeśli piszesz przetwarzanie wejścia/wyjścia. Zwykle nie muszą pochodzić z tych klas. Jeśli używasz struktury aplikacji, domyślna implementacja metody **Otwórz** i **Zapisz** polecenia na **pliku** menu będzie obsługiwać we/wy (za pomocą klasy `CArchive`), tak długo, jak zastąpić dokumentu `Serialize` funkcję, aby podać szczegółowe informacje dotyczące sposobu dokumentu serializuje jego zawartość. Aby uzyskać więcej informacji na temat klasy plików i serializacji, zobacz artykuł [pliki w MFC](../mfc/files-in-mfc.md) oraz artykuł [serializacji](../mfc/serialization-in-mfc.md).

[CFile](../mfc/reference/cfile-class.md)<br/>
Udostępnia interfejs pliku do plików binarnych dysku.

[CStdioFile](../mfc/reference/cstdiofile-class.md)<br/>
Udostępnia `CFile` interfejsu do buforowanego strumienia plików dysku, zazwyczaj w trybie tekstowym.

[CMemFile](../mfc/reference/cmemfile-class.md)<br/>
Udostępnia `CFile` interfejsu do plików w pamięci.

[CSharedFile](../mfc/reference/csharedfile-class.md)<br/>
Udostępnia `CFile` interfejsu do udostępnionych plików w pamięci.

[COleStreamFile](../mfc/reference/colestreamfile-class.md)<br/>
COM używa `IStream` interfejsu, aby zapewnić `CFile` dostęp do plików złożona (c).

[CSocketFile](../mfc/reference/csocketfile-class.md)<br/>
Udostępnia `CFile` interfejs do gniazda Windows.

## <a name="related-classes"></a>Klasy pokrewne

[CArchive](../mfc/reference/carchive-class.md)<br/>
Współpracuje z `CFile` obiektu do zaimplementowania trwałego magazynu obiektów za pomocą serializacji (zobacz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).

[CArchiveException](../mfc/reference/carchiveexception-class.md)<br/>
Wyjątek archiwum.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Wyjątek zorientowane na plik.

[CFileDialog](../mfc/reference/cfiledialog-class.md)<br/>
Zawiera standardowe okno dialogowe Otwieranie lub zapisywanie pliku.

[CRecentFileList](../mfc/reference/crecentfilelist-class.md)<br/>
Obsługuje listy ostatnio używanych (MRU) pliku.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

