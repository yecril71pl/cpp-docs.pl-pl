---
title: Pliki w MFC | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64a8df138ef0d581bcc93bf836ee0935a634983d
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930506"
---
# <a name="files-in-mfc"></a>Pliki w MFC
Klasa w Microsoft Foundation Class Library (MFC), [cfile —](../mfc/reference/cfile-class.md) obsługi operacji We/Wy pliku normalnego. Tej rodziny artykułów wyjaśniono, jak otwieranie i zamykanie plików, a także odczytywania i zapisywania danych do tych plików. Również zawiera omówienie stanu operacji na plikach. Opis sposobu korzystania z funkcji serializacji obiektów MFC jako alternatywny sposób odczytywania i zapisywania danych w plikach, zobacz artykuł [szeregowanie](../mfc/serialization-in-mfc.md).  
  
> [!NOTE]
>  Jeśli używasz MFC `CDocument` obiekty, w ramach jest znaczną część pracy serializacji dla Ciebie. W szczególności tworzone i używane w ramach `CFile` obiektu. Trzeba napisać kod w zastąpienia z `Serialize` funkcji członkowskiej klasy `CDocument`.  
  
 `CFile` Klasa udostępnia interfejs dla operacji na plikach binarnych ogólnego przeznaczenia. `CStdioFile` i `CMemFile` pochodną klasy `CFile` i `CSharedFile` klasą pochodną `CMemFile` podać wyspecjalizowanego usług plików.  
  
 Aby uzyskać więcej informacji na temat rozwiązań alternatywnych do obsługi plików MFC, zobacz [Obsługa plików](../c-runtime-library/file-handling.md) w *odwołanie do biblioteki wykonawczej*.  
  
 Informacje o pochodnych `CFile` klas, zobacz [diagram hierarchii MFC](../mfc/hierarchy-chart.md).  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić  
 *Cfile — użycie*  
  
-   [Otwórz plik z cfile —](../mfc/opening-files.md)  
  
-   [Odczyt i zapis plików z cfile —](../mfc/reading-and-writing-files.md)  
  
-   [Zamknij plik z cfile —](../mfc/closing-files.md)  
  
-   [Stan dostępu do pliku z cfile —](../mfc/accessing-file-status.md)  
  
 *Użyj MFC serializacji (trwałości obiektu)*  
  
-   [Tworzenie klasy możliwej do serializacji](../mfc/serialization-making-a-serializable-class.md)  
  
-   [Szeregowania obiektu za pomocą obiektu CArchive](../mfc/serialization-serializing-an-object.md)  
  
-   [Tworzenia obiektu CArchive](../mfc/two-ways-to-create-a-carchive-object.md)  
  
-   [CArchive — użyj <\< i >> operatorów](../mfc/using-the-carchive-output-and-input-operators.md)  
  
-   [Przechowywanie i ładowanie pochodzi z obiektu CObject obiektów za pomocą archiwum i CObject — obiekty](../mfc/storing-and-loading-cobjects-via-an-archive.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia](../mfc/mfc-concepts.md)   
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)   
 [CArchive — klasa](../mfc/reference/carchive-class.md)   
 [Klasa CObject](../mfc/reference/cobject-class.md)
