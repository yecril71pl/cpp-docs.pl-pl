---
title: Otwieranie plików
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: 6119bf922b05c30a14d8421800e3931c4a038779
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375960"
---
# <a name="opening-files"></a>Otwieranie plików

W MFC najczęstszym sposobem otwierania pliku jest proces dwuetapowy.

#### <a name="to-open-a-file"></a>Aby otworzyć plik

1. Utwórz obiekt pliku bez określania flag ścieżki lub uprawnień.

   Zwykle tworzy się obiekt pliku, deklarując zmienną [CFile](../mfc/reference/cfile-class.md) w ramce stosu.

1. Wywołanie funkcji [Otwórz](../mfc/reference/cfile-class.md#open) element członkowski dla obiektu pliku, podając flagi ścieżki i uprawnień.

   Zwracana wartość `Open` będzie niezerowa, jeśli plik został pomyślnie otwarty lub 0, jeśli nie można otworzyć określonego pliku. Funkcja `Open` elementu członkowskiego jest prototypowana w następujący sposób:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Otwarte flagi określają, które uprawnienia, takie jak tylko do odczytu, chcesz dla pliku. Możliwe wartości flag są definiowane jako wyliczone stałe w `CFile` klasie, więc są kwalifikowane za pomocą " "`CFile::`jak w `CFile::modeRead`. Użyj `CFile::modeCreate` flagi, jeśli chcesz utworzyć plik.

W poniższym przykładzie pokazano, jak utworzyć nowy plik z uprawnieniami do odczytu/zapisu (zastępując poprzedni plik tą samą ścieżką):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> W tym przykładzie tworzy i otwiera plik. Jeśli występują problemy, `Open` wywołanie `CFileException` może zwrócić obiekt w jego ostatnim parametrze, jak pokazano poniżej. Makro TRACE drukuje zarówno nazwę pliku, jak i kod wskazujący przyczynę niepowodzenia. Można wywołać `AfxThrowFileException` funkcję, jeśli potrzebujesz bardziej szczegółowego raportowania błędów.

## <a name="see-also"></a>Zobacz też

[Klasa CFile](../mfc/reference/cfile-class.md)<br/>
[Plik C::Otwórz](../mfc/reference/cfile-class.md#open)<br/>
[Pliki](../mfc/files-in-mfc.md)
