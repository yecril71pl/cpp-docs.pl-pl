---
title: Pliki pomocy (Pomoc HTML)
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], HTML Help files
ms.assetid: d30a1b1b-318f-4a78-8b60-93da53a224a8
ms.openlocfilehash: cde4809fa270e66081088d68d806e637f64e5344
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270216"
---
# <a name="help-files-html-help"></a>Pliki pomocy (Pomoc HTML)

Następujące pliki są tworzone podczas dodawania typu pomocy HTML, pomoc techniczną do aplikacji, wybierając **pomocy kontekstowej** pole wyboru, a następnie wybierając **format Pomocy HTML** w [Funkcje zaawansowane](../../mfc/reference/advanced-features-mfc-application-wizard.md) strony Kreatora aplikacji MFC.

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*hhp|*Projname*\hlp|pliki Pomocy w formacie HTML|Plik projektu pomocy. Zawiera ona dane potrzebne do skompilowania plików pomocy w postaci pliku .hxs lub plik chm.|
|*Projname*.hhk|*Projname*\hlp|pliki Pomocy w formacie HTML|Zawiera indeks tematów Pomocy.|
|*Projname*.hhc|*Projname*\hlp|pliki Pomocy w formacie HTML|Zawartość pomocy projektu.|
|Makehtmlhelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy, gdy projekt jest skompilowany.|
|Afxcore.htm|*Projname*\hlp|Tematy Pomocy HTML|Zawiera standardowe tematy pomocy dla standardowych poleceń MFC i obiektów ekranu. Dodaj tematy pomocy do tego pliku.|
|Afxprint.htm|*Projname*\hlp|Tematy Pomocy HTML|Zawiera tematy pomocy dla polecenia drukowania.|
|\*.jpg; \*.gif|*Projname*\hlp\Images|Pliki zasobów|Zawiera obrazy do różnych tematów wygenerowany plik.|

## <a name="see-also"></a>Zobacz także

[Typy plików utworzonych dla projektów Visual C++](file-types-created-for-visual-cpp-projects.md)
