---
title: Pomoc plików (Pomoc HTML) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d180fe4f9cf1baf26b27423ffda975bfe0fe85ba
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "33325078"
---
# <a name="help-files-html-help"></a>Pliki pomocy (Pomoc HTML)
Następujące pliki zostaną utworzone po dodaniu rodzaj pomocy HTML pomoc techniczna do aplikacji przez wybranie **pomocy kontekstowej** pole wyboru, a następnie wybierając **format Pomocy HTML** w [Funkcje zaawansowane](../mfc/reference/advanced-features-mfc-application-wizard.md) Kreatora aplikacji MFC.  
  
|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*hhp|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|pliki Pomocy w formacie HTML|Plik projektu pomocy. Zawiera dane wymagane do kompilacji pliki pomocy do pliku .hxs lub plik .chm.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.hhk|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|pliki Pomocy w formacie HTML|Zawiera indeks tematów Pomocy.|  
|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*.hhc|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|pliki Pomocy w formacie HTML|Zawartość pomocy projektu.|  
|Makehtmlhelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy w przypadku, gdy kompilowany jest projekt.|  
|Afxcore.htm|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Tematy Pomocy HTML|Zawiera standardowe tematy pomocy dla standardowych poleceń MFC i obiektów ekranu. Dodaj tematy pomocy do tego pliku.|  
|Afxprint.htm|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp|Tematy Pomocy HTML|Zawiera tematy pomocy dla polecenia drukowania.|  
|\*.jpg; \*.gif|*Nazwa_projektu.nazwa_modułu.nazwa_procedury*\hlp\Images|Pliki zasobów|Zawiera obrazy do różnych tematów wygenerowanego pliku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)