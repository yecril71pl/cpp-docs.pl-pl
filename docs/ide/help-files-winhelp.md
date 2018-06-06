---
title: Pliki pomocy (WinHelp) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 505506c7f3a14a73c6b0c859a70938fee3eed69e
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33331548"
---
# <a name="help-files-winhelp"></a>Pliki pomocy (WinHelp)
Następujące pliki zostaną utworzone po dodaniu typ WinHelp pomoc techniczna do aplikacji przez wybranie **pomocy kontekstowej** pole wyboru, a następnie wybierając **WinHelp format** w [Funkcje zaawansowane](../mfc/reference/advanced-features-mfc-application-wizard.md) Kreatora aplikacji MFC.  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.hpj|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki źródłowe|Plik projektu pomocy używany przez kompilator pomocy do tworzenia programu lub pliku Pomocy formantu.|  
|*Projname*.rtf|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki pomocy|Zawiera tematy dotyczące szablonu, które można edytować i informacji o dostosowywaniu pliku .hpj.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.cnt|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki pomocy|Udostępnia struktury **zawartość** okna w Pomocy systemu Windows.|  
|Makehelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy w przypadku, gdy kompilowany jest projekt.|  
|Print.rtf|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki pomocy|Utworzone, jeśli projekt zawiera obsługę drukowania (ustawienie domyślne). Opisuje drukowania poleceń i okien dialogowych.|  
|*.bmp|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki zasobów|Zawiera obrazy do różnych tematów wygenerowanego pliku.|  
  
 WinHelp pomocy technicznej można dodać do projektu kontrolki ActiveX MFC, wybierając **Generowanie plików Pomocy** w [ustawienia aplikacji](../mfc/reference/application-settings-mfc-activex-control-wizard.md) kartę Kreator formantów MFC ActiveX. Następujące pliki są dodawane do projektu po dodaniu pomoc techniczna do kontrolki MFC ActiveX:  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.hpj|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki źródłowe|Plik projektu używany przez kompilator pomocy do tworzenia programu lub pliku Pomocy formantu.|  
|*Projname*.rtf|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Projekt|Zawiera tematy dotyczące szablonu, które można edytować i informacji o dostosowywaniu pliku .hpj.|  
|Makehelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy w przypadku, gdy kompilowany jest projekt.|  
|Bullet.bmp|*Projname*|Pliki zasobów|Używany przez standardowy plik pomoc do reprezentowania punktowane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)