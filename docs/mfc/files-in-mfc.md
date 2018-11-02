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
ms.openlocfilehash: 815239b0d4de1938a810153cb98f39b2642b6e2d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50459335"
---
# <a name="files-in-mfc"></a>Pliki w MFC

Klasy w Microsoft Foundation Class Library (MFC), [CFile](../mfc/reference/cfile-class.md) obsługuje operacje na plikach normalnych operacji We/Wy. Tej rodziny artykuły wyjaśnia, jak otwieranie i zamykanie plików, a także do odczytu i zapisu danych tych plików. Omawia także stan operacji na plikach. Aby uzyskać opis sposobu używania funkcji opartej na obiektach serializacji MFC jako alternatywny sposób odczytywania i zapisywania danych w plikach, zobacz artykuł [serializacji](../mfc/serialization-in-mfc.md).

> [!NOTE]
>  Kiedy używać MFC `CDocument` obiektów, w ramach wykonuje znaczną część pracy serializacji dla Ciebie. W szczególności, tworzy i wykorzystuje w ramach `CFile` obiektu. Trzeba napisać kod w zastąpienie metody `Serialize` funkcji składowej klasy typu `CDocument`.

`CFile` Klasa udostępnia interfejs dla operacji na plikach binarnych ogólnego przeznaczenia. `CStdioFile` i `CMemFile` klasy pochodne `CFile` i `CSharedFile` klasą pochodną `CMemFile` Podaj bardziej wyspecjalizowane usług plików.

Aby uzyskać więcej informacji na temat rozwiązania alternatywne do obsługi plików MFC, zobacz [Obsługa plików](../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.

Aby uzyskać informacje pochodzące `CFile` klas, zobacz [MFC wykresu hierarchii](../mfc/hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić

*Użyj CFile*

- [Otwórz plik przy użyciu CFile](../mfc/opening-files.md)

- [Odczytywanie i zapisywanie plików za pomocą CFile](../mfc/reading-and-writing-files.md)

- [Zamknij plik z CFile](../mfc/closing-files.md)

- [Stan pliku dostępu za pomocą CFile](../mfc/accessing-file-status.md)

*Użyj MFC serializacji (trwałość obiektów)*

- [Utwórz klasę do serializacji](../mfc/serialization-making-a-serializable-class.md)

- [Serializacja obiektu za pomocą obiektu CArchive](../mfc/serialization-serializing-an-object.md)

- [Tworzenia obiektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md)

- [Użyj obiektu CArchive <\< i >> operatorów](../mfc/using-the-carchive-output-and-input-operators.md)

- [Store i ładowanie obiektów CObject i pochodzących z obiektu CObject obiektów za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Zobacz też

[Pojęcia](../mfc/mfc-concepts.md)<br/>
[Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)<br/>
[Klasa CArchive](../mfc/reference/carchive-class.md)<br/>
[Klasa CObject](../mfc/reference/cobject-class.md)
