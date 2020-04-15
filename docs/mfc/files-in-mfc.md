---
title: Pliki w MFC
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 3a99c4143bbd27ba765b0289b80be8870a940f63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365313"
---
# <a name="files-in-mfc"></a>Pliki w MFC

W bibliotece klas Microsoft Foundation Class Library (MFC) klasa [CFile](../mfc/reference/cfile-class.md) obsługuje normalne operacje we/wy pliku. Ta rodzina artykułów wyjaśnia, jak otwierać i zamykać pliki, a także odczytywać i zapisywać dane do tych plików. Omówiono również operacje stanu pliku. Aby uzyskać opis sposobu używania funkcji serializacji opartej na obiektach MFC jako alternatywnego sposobu odczytu i zapisu danych w plikach, zobacz artykuł [Serializacja](../mfc/serialization-in-mfc.md).

> [!NOTE]
> Korzystając z obiektów `CDocument` MFC, ramach wykonuje wiele pracy serializacji dla Ciebie. W szczególności ramach tworzy i `CFile` używa obiektu. Wystarczy napisać kod w nadpisywać `Serialize` funkcję elementu `CDocument`członkowskiego klasy .

Klasa `CFile` zapewnia interfejs do operacji plików binarnych ogólnego przeznaczenia. I `CStdioFile` `CMemFile` klasy pochodzące `CFile` z `CSharedFile` i klasy `CMemFile` pochodzące z dostarczania bardziej wyspecjalizowanych usług plików.

Aby uzyskać więcej informacji na temat alternatyw dla obsługi plików MFC, zobacz [Obsługa plików](../c-runtime-library/file-handling.md) w *odwołaniu do biblioteki w czasie wykonywania*.

Aby uzyskać informacje `CFile` na temat klas pochodnych, zobacz [wykres hierarchii MFC](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

*Użyj pliku CFile*

- [Otwieranie pliku za pomocą pliku CFile](../mfc/opening-files.md)

- [Odczytywanie i pisanie pliku za pomocą pliku CFile](../mfc/reading-and-writing-files.md)

- [Zamykanie pliku za pomocą pliku CFile](../mfc/closing-files.md)

- [Stan pliku programu Access za pomocą pliku CFile](../mfc/accessing-file-status.md)

*Użyj serializacji MFC (trwałość obiektu)*

- [Tworzenie klasy serializable](../mfc/serialization-making-a-serializable-class.md)

- [Serializacja obiektu za pomocą CArchive obiektu](../mfc/serialization-serializing-an-object.md)

- [Tworzenie obiektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Użyj operatorów <\< <i >> C](../mfc/using-the-carchive-output-and-input-operators.md)

- [Przechowywanie i ładowanie obiektów CObjects i CObject za pośrednictwem archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CArchive](../mfc/reference/carchive-class.md)<br/>
[Klasa CObject](../mfc/reference/cobject-class.md)
