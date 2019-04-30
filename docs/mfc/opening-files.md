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
ms.openlocfilehash: dab7a680d9b33a6e334da99a045b709fe00f215c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394484"
---
# <a name="opening-files"></a>Otwieranie plików

W MFC najbardziej popularny sposób, aby otworzyć plik jest procesem dwuetapowym.

#### <a name="to-open-a-file"></a>Aby otworzyć plik

1. Utwórz obiekt pliku bez określania flagi ścieżki lub uprawnienia.

   Zazwyczaj Tworzenie obiektu pliku przez zadeklarowanie [CFile](../mfc/reference/cfile-class.md) zmiennej na ramce stosu.

1. Wywołaj [Otwórz](../mfc/reference/cfile-class.md#open) funkcja elementu członkowskiego dla obiektu pliku dostarczenie flagi ścieżkę i uprawnień.

   Wartość zwracana dla `Open` będzie różna od zera, jeśli plik został pomyślnie otwarty lub równa 0, jeśli nie można otworzyć określonego pliku. `Open` Funkcja członkowska jest prototypowane w następujący sposób:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Otwórz flagi określić uprawnienia, takie jak tylko do odczytu, ma dla pliku. Możliwe wartości flag są definiowane jako stałych wyliczeniowych w ramach `CFile` klasy, dzięki czemu są one kwalifikowana za pomocą "`CFile::`" jak w `CFile::modeRead`. Użyj `CFile::modeCreate` flagę, jeśli chcesz utworzyć plik.

Poniższy przykład pokazuje, jak utworzyć nowy plik z uprawnieniami odczytu/zapisu (zastępując dowolnego poprzedniego pliku o takiej samej ścieżce):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
>  W tym przykładzie tworzy i otwiera plik. Jeśli wystąpią problemy, `Open` wywołanie może zwrócić `CFileException` obiektu w jego ostatni parametr, jak pokazano poniżej. TRACE — makro drukuje kod wskazujący przyczynę błędu i nazwę pliku. Możesz wywołać `AfxThrowFileException` działać, jeśli potrzebujesz bardziej szczegółowe raportowanie błędów.

## <a name="see-also"></a>Zobacz także

[Klasa CFile](../mfc/reference/cfile-class.md)<br/>
[CFile::Open](../mfc/reference/cfile-class.md#open)<br/>
[Pliki](../mfc/files-in-mfc.md)
