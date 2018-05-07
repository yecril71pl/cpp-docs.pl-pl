---
title: Klasy-O plików | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b11996aadd58b456aa919d4ff888c783b4ba486e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="file-io-classes"></a>Klasy we/wy plików
Te klasy zapewnia interfejs do plików dysku tradycyjnych, pliki w pamięci Active strumieni i Windows sockets. Wszystkie klasy pochodne `CFile` mogą być używane z `CArchive` obiektu w celu wykonania serializacji.  
  
 Użyj następujących klas, szczególnie `CArchive` i `CFile`, jeśli piszesz przetwarzania wejścia/wyjścia. Zwykle nie trzeba pochodzić z tych klas. Jeśli używasz struktury aplikacji, domyślne implementacje **Otwórz** i **zapisać** polecenia w **pliku** menu będzie obsługiwać We/Wy plików (za pomocą klasy `CArchive`), tak długo, jak zastąpić dokumentu `Serialize` funkcji, aby podać szczegółowe informacje o jak dokument serializuje jego zawartość. Aby uzyskać więcej informacji na temat klasy plików i serializacji, zobacz artykuł [pliki w MFC](../mfc/files-in-mfc.md) i artykułu [szeregowanie](../mfc/serialization-in-mfc.md).  
  
 [Cfile —](../mfc/reference/cfile-class.md)  
 Udostępnia interfejs pliku do plików binarnych dysku.  
  
 [CStdioFile](../mfc/reference/cstdiofile-class.md)  
 Udostępnia `CFile` interfejs do plików dysku buforowanego strumienia, zazwyczaj w trybie tekstowym.  
  
 [CMemFile](../mfc/reference/cmemfile-class.md)  
 Udostępnia `CFile` interfejs do plików w pamięci.  
  
 [CSharedFile](../mfc/reference/csharedfile-class.md)  
 Udostępnia `CFile` interfejs do udostępnionych plików w pamięci.  
  
 [COleStreamFile](../mfc/reference/colestreamfile-class.md)  
 Używa modelu COM `IStream` interfejsu w celu zapewnienia `CFile` dostępu do plików złożonych.  
  
 [CSocketFile](../mfc/reference/csocketfile-class.md)  
 Udostępnia `CFile` interfejs do gniazda systemu Windows.  
  
## <a name="related-classes"></a>Klasy pokrewne  
 [CArchive](../mfc/reference/carchive-class.md)  
 Współpracuje z `CFile` obiektu do zaimplementowania magazynu trwałego dla obiektów za pomocą serializacji (zobacz [CObject::Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Wystąpił wyjątek archiwum.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Wyjątek zorientowane na plik.  
  
 [CFileDialog](../mfc/reference/cfiledialog-class.md)  
 Zawiera standardowe okno dialogowe Otwieranie lub zapisywanie pliku.  
  
 [CRecentFileList](../mfc/reference/crecentfilelist-class.md)  
 Przechowuje listy ostatnio używanych (MRU) pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

