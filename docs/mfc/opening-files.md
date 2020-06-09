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
ms.openlocfilehash: 73407eba802b7640e880b821144954fa6442f177
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622161"
---
# <a name="opening-files"></a>Otwieranie plików

W MFC, najbardziej typowym sposobem otwierania pliku jest proces dwuetapowy.

#### <a name="to-open-a-file"></a>Aby otworzyć plik

1. Utwórz obiekt pliku bez określania ścieżki lub flag uprawnień.

   Zazwyczaj tworzysz obiekt pliku, deklarując zmienną [CFile](reference/cfile-class.md) w ramce stosu.

1. Wywołaj funkcję [Open](reference/cfile-class.md#open) member dla obiektu File, podając ścieżkę i flagi uprawnień.

   Wartość zwracana dla programu `Open` będzie różna od zera, jeśli plik został pomyślnie otwarty lub 0, jeśli nie można otworzyć określonego pliku. `Open`Funkcja członkowska jest prototypem:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Otwarte flagi określają, które uprawnienia, takie jak tylko do odczytu, mają być dla tego pliku. Możliwe wartości flagi są zdefiniowane jako stałe wyliczane w obrębie `CFile` klasy, dzięki czemu są kwalifikowane `CFile::` jako "" w `CFile::modeRead` . Użyj `CFile::modeCreate` flagi, jeśli chcesz utworzyć plik.

Poniższy przykład pokazuje, jak utworzyć nowy plik z uprawnieniem do odczytu/zapisu (zastępujący poprzedni plik z tą samą ścieżką):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> Ten przykład tworzy i otwiera plik. Jeśli występują problemy, `Open` wywołanie może zwrócić `CFileException` obiekt w ostatnim parametrze, jak pokazano poniżej. Makro śledzenia drukuje zarówno nazwę pliku, jak i kod wskazujący przyczynę niepowodzenia. Możesz wywołać tę `AfxThrowFileException` funkcję, jeśli potrzebujesz bardziej szczegółowych informacji o raportowaniu błędów.

## <a name="see-also"></a>Zobacz też

[Klasa CFile](reference/cfile-class.md)<br/>
[CFile:: Open](reference/cfile-class.md#open)<br/>
[Files](files-in-mfc.md)
