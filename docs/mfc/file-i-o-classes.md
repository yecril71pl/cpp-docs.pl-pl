---
title: Klasy we/wy plików
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
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
ms.openlocfilehash: 2fcf4dfc1388df0df2bc25928ec8541486c6bb2d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615673"
---
# <a name="file-io-classes"></a>Klasy we/wy plików

Klasy te zapewniają interfejs do tradycyjnych plików dyskowych, plików w pamięci, aktywnych strumieni i gniazd Windows Sockets. Wszystkie klasy pochodne `CFile` mogą być używane z `CArchive` obiektem do wykonania serializacji.

Użyj następujących klas, szczególnie `CArchive` i `CFile` , jeśli piszesz własne przetwarzanie danych wejściowych/wyjściowych. Zwykle nie trzeba dziedziczyć z tych klas. Jeśli używasz struktury aplikacji, domyślne implementacje poleceń **Otwórz** i **Zapisz** w menu **plik** będą obsługiwać we/wy pliku (przy użyciu klasy `CArchive` ), o ile zastąpisz `Serialize` funkcję dokumentu w celu dostarczenia szczegółowych informacji o tym, jak dokument serializować jego zawartość. Aby uzyskać więcej informacji na temat klas plików i serializacji, zobacz [pliki artykułów w MFC](files-in-mfc.md) i [Serializacja](serialization-in-mfc.md)artykułu.

[CFile](reference/cfile-class.md)<br/>
Udostępnia interfejs plików na dyskach binarnych.

[CStdioFile](reference/cstdiofile-class.md)<br/>
Udostępnia `CFile` interfejs do buforowanych plików dysku strumienia, zwykle w trybie tekstowym.

[CMemFile](reference/cmemfile-class.md)<br/>
Udostępnia `CFile` interfejs do plików w pamięci.

[CSharedFile](reference/csharedfile-class.md)<br/>
Udostępnia `CFile` interfejs do współużytkowanych plików w pamięci.

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Używa interfejsu COM, `IStream` Aby zapewnić `CFile` dostęp do plików złożonych.

[CSocketFile](reference/csocketfile-class.md)<br/>
Udostępnia `CFile` interfejs do gniazda systemu Windows.

## <a name="related-classes"></a>Powiązane klasy

[CArchive](reference/carchive-class.md)<br/>
Współdziała z `CFile` obiektem, aby zaimplementować trwały magazyn dla obiektów za pomocą serializacji (zobacz [CObject::](reference/cobject-class.md#serialize)Serialization).

[CArchiveException](reference/carchiveexception-class.md)<br/>
Wyjątek archiwum.

[CFileException](reference/cfileexception-class.md)<br/>
Wyjątek zorientowany na pliki.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Zawiera standardowe okno dialogowe umożliwiające otwarcie lub zapisanie pliku.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Zachowuje ostatnio używaną listę plików (MRU).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](class-library-overview.md)
