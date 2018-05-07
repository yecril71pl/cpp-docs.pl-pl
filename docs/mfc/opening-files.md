---
title: Otwieranie plików | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 379449469d37f01c7c0fd225688a019eaec9e977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="opening-files"></a>Otwieranie plików
W MFC najczęściej próbę otwarcia pliku jest procesem dwuetapowym.  
  
#### <a name="to-open-a-file"></a>Aby otworzyć plik  
  
1.  Tworzenie obiektu pliku bez określenia flagi ścieżki lub uprawnienia.  
  
     Zazwyczaj Tworzenie obiektu pliku przez zadeklarowanie [cfile —](../mfc/reference/cfile-class.md) zmiennej w ramce stosu.  
  
2.  Wywołanie [Otwórz](../mfc/reference/cfile-class.md#open) funkcji członkowskiej dla obiektu pliku, podając flagi ścieżkę i uprawnienia.  
  
     Wartość zwracana `Open` będzie różna od zera, jeśli plik został pomyślnie otwarty lub 0, jeśli nie można otworzyć określonego pliku. `Open` Funkcja członkowska jest prototypowana w następujący sposób:  
  
     `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`  
  
     Flagi Otwórz określić które uprawnienia tylko do odczytu, ma dla pliku. Możliwe wartości flag są zdefiniowane jako wyliczone stałe w `CFile` klasy, dzięki czemu są one kwalifikowanej z "`CFile::`" jak w `CFile::modeRead`. Użyj `CFile::modeCreate` Flaga, jeśli chcesz utworzyć plik.  
  
 Poniższy przykład przedstawia sposób tworzenia nowego pliku z uprawnieniami odczytu/zapisu (zastępując wszelkie poprzednie plik o takiej samej ścieżce):  
  
 [!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]  
  
> [!NOTE]
>  W tym przykładzie tworzy i otwiera plik. Jeśli występują problemy, `Open` może zwrócić wywołanie `CFileException` obiektu w jej ostatni parametr, jak pokazano poniżej. `TRACE` Makro wyświetla kod wskazujący przyczynę błędu i nazwę pliku. Możesz wywołać `AfxThrowFileException` funkcji, jeśli potrzebujesz bardziej szczegółowe raportowanie błędów.  
  
## <a name="see-also"></a>Zobacz też  
 [Cfile — klasa](../mfc/reference/cfile-class.md)   
 [CFile::Open](../mfc/reference/cfile-class.md#open)   
 [Pliki](../mfc/files-in-mfc.md)

