---
title: Pliki pomocy (WinHelp) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a5036aa329c0b4004bd7ada724c62e1a1669f050
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="help-files-winhelp"></a>Pliki pomocy (WinHelp)
Następujące pliki zostaną utworzone po dodaniu typ WinHelp pomoc techniczna do aplikacji przez wybranie **pomocy kontekstowej** pole wyboru, a następnie wybierając **WinHelp format** w [Funkcje zaawansowane](../mfc/reference/advanced-features-mfc-application-wizard.md) Kreatora aplikacji MFC.  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.hpj|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki źródłowe|Plik projektu pomocy używany przez kompilator pomocy do tworzenia programu lub pliku Pomocy formantu.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*RTF|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki pomocy|Zawiera tematy dotyczące szablonu, które można edytować i informacji o dostosowywaniu pliku .hpj.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.cnt|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki pomocy|Udostępnia struktury **zawartość** okna w Pomocy systemu Windows.|  
|Makehelp.bat|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy w przypadku, gdy kompilowany jest projekt.|  
|Print.rtf|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki pomocy|Utworzone, jeśli projekt zawiera obsługę drukowania (ustawienie domyślne). Opisuje drukowania poleceń i okien dialogowych.|  
|*.bmp|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki zasobów|Zawiera obrazy do różnych tematów wygenerowanego pliku.|  
  
 WinHelp pomocy technicznej można dodać do projektu kontrolki ActiveX MFC, wybierając **Generowanie plików Pomocy** w [ustawienia aplikacji](../mfc/reference/application-settings-mfc-activex-control-wizard.md) kartę Kreator formantów MFC ActiveX. Następujące pliki są dodawane do projektu po dodaniu pomoc techniczna do kontrolki MFC ActiveX:  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.hpj|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Pliki źródłowe|Plik projektu używany przez kompilator pomocy do tworzenia programu lub pliku Pomocy formantu.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*RTF|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Project|Zawiera tematy dotyczące szablonu, które można edytować i informacji o dostosowywaniu pliku .hpj.|  
|Makehelp.bat|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy w przypadku, gdy kompilowany jest projekt.|  
|Bullet.bmp|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*|Pliki zasobów|Używany przez standardowy plik pomoc do reprezentowania punktowane.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)