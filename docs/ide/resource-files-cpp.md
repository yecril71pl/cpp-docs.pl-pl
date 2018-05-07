---
title: Pliki zasobów (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0c295b9a3aa4996cdcd2afb17b5a4ff4c90c1159
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)
Zasoby są elementów interfejsu, które zawierają informacje dla użytkownika. Mapy bitowe, ikony paski narzędzi i kursory są wszystkie zasoby. Do wykonania akcji, takich jak wybierając z menu lub wprowadzania danych w oknie dialogowym można manipulować niektórych zasobów.  
  
 Zobacz [pracy z zasobami](../windows/working-with-resource-files.md) Aby uzyskać więcej informacji.  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.rc|*Projname*|Pliki źródłowe|Plik skryptu zasobu dla projektu. Plik skryptu zasobu zawiera następujące polecenie, w zależności od typu Projekt i obsługa wybrana dla projektu (na przykład paski narzędzi, okna dialogowe lub HTML):<br /><br /> -Definicja menu domyślne.<br />-Tabele akceleratora i ciąg.<br />-Domyślne **o** okno dialogowe.<br />-Innych oknach dialogowych.<br />-Plik ikony (res\\*nazwa_projektu.nazwa_modułu.nazwa_procedury*.ico).<br />— Informacje o wersji.<br />-Map bitowych.<br />-Paska narzędzi.<br />— Pliki HTML.<br /><br /> Plik zasobów zawiera plik Afxres.rc dla standardowe zasoby MFC.|  
|Resource.h|*Projname*|Pliki nagłówkowe|Plik nagłówka zasobu zawiera definicje dla zasobów używanych przez projekt.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.rc2|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\res|Pliki źródłowe|Plik skryptu zawierający dodatkowe zasoby używane przez projekt. Można dołączyć plik .rc2 w górnej części pliku .rc projektu.<br /><br /> Plik .rc2 jest przydatna przy tym zasoby używane przez kilka różnych projektów. Zamiast konieczności tworzenia tych samych zasobów dla różnych projektów, można umieścić je w pliku .rc2 i dołączyć plik .rc2 w plik .rc głównego.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.def|*Projname*|Pliki źródłowe|Plik definicji modułu dla projektu biblioteki DLL. W przypadku formantu zawiera nazwę i opis formantu oraz Rozmiar sterty czasu wykonywania.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*ICO|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\res|Pliki zasobów|Plik ikony do projektu lub kontrolki. Ta ikona jest wyświetlana, gdy aplikacja jest zminimalizowany. Jest on również używany w aplikacji **o** pola. Domyślnie MFC zawiera ikonę MFC i ATL zawiera ikonę ATL.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*Doc.ico|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\res|Pliki zasobów|Plik ikony do projektu MFC z obsługą dla architektury dokument/widok.|  
|Toolbar.bmp|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\res|Pliki zasobów|Plik mapy bitowej reprezentujący aplikacji lub formantu paska narzędzi lub palety. Ta mapa bitowa znajduje się w pliku zasobów projektu. Początkowa narzędzi i paskiem stanu są skonstruowane w **cmainframe —** klasy.|  
|Ribbon.mfcribbon ms|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\res|Pliki zasobów|Plik zasobu, który zawiera kod XML, definiujący przycisków, formantów i atrybutów na Wstążce. Aby uzyskać więcej informacji, zobacz [projektanta wstążki (MFC)](../mfc/ribbon-designer-mfc.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)