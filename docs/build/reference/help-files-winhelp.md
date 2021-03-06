---
title: Pliki pomocy (WinHelp)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], WinHelp files
ms.assetid: 4fdcbd66-66b0-4866-894a-fd7b4c2557e4
ms.openlocfilehash: 6810b3f608b9fa7892b686d72056994fb98c92db
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707466"
---
# <a name="help-files-winhelp"></a>Pliki pomocy (WinHelp)

Następujące pliki są tworzone podczas dodawania typu WinHelp — pomoc techniczna do aplikacji, wybierając **pomocy kontekstowej** pole wyboru, a następnie wybierając **WinHelp format** w [Funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) strony Kreatora aplikacji MFC.

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hpj|*Projname*\hlp|Pliki źródłowe|Plik projektu pomocy używaną przez kompilatora plików pomocy do tworzenia programu lub pliku Pomocy formantu.|
|*Projname*.rtf|*Projname*\hlp|Pliki pomocy|Zawiera tematy szablonu, które można edytować i informacji o dostosowywaniu .hpj pliku.|
|*Projname*.cnt|*Projname*\hlp|Pliki pomocy|Dostarcza strukturę dla **zawartość** okna w Pomocy programu Windows.|
|Makehelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy, gdy projekt jest skompilowany.|
|Print.rtf|*Projname*\hlp|Pliki pomocy|Utworzone, jeśli projekt zawiera obsługę drukowania (ustawienie domyślne). Opis polecenia drukowania i oknach dialogowych.|
|*.bmp|*Projname*\hlp|Pliki zasobów|Zawiera obrazy do różnych tematów wygenerowany plik.|

WinHelp pomocy technicznej można dodać do projektu kontrolki ActiveX MFC, wybierając **Generuj pliki Pomocy** w [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-activex-control-wizard.md) kartę Kreator kontrolek ActiveX MFC. Następujące pliki są dodawane do projektu po dodaniu pomoc techniczna do kontrolki MFC ActiveX:

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.hpj|*Projname*\hlp|Pliki źródłowe|Plik projektu, używany przez kompilatora plików pomocy do utworzenia programu, lub plik Pomocy formantu.|
|*Projname*.rtf|*Projname*\hlp|Projekt|Zawiera tematy szablonu, które można edytować i informacji o dostosowywaniu .hpj pliku.|
|Makehelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy, gdy projekt jest skompilowany.|
|Bullet.bmp|*Projname*|Pliki zasobów|Używane przez standardowy plik tematów do reprezentowania list punktowanych.|

## <a name="see-also"></a>Zobacz także

[Plik typy utworzone dla programu Visual Studio C++ projektów](file-types-created-for-visual-cpp-projects.md)
