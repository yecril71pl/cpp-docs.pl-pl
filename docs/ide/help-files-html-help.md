---
title: Pliki pomocy (Pomoc HTML) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 04d3171f1bba6b803c68b7a3b753cc70825671bb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383548"
---
# <a name="help-files-html-help"></a>Pliki pomocy (Pomoc HTML)

Następujące pliki są tworzone podczas dodawania typu pomocy HTML, pomoc techniczną do aplikacji, wybierając **pomocy kontekstowej** pole wyboru, a następnie wybierając **format Pomocy HTML** w [Funkcje zaawansowane](../mfc/reference/advanced-features-mfc-application-wizard.md) strony Kreatora aplikacji MFC.

|Nazwa pliku|Lokalizacja katalogu|Lokalizacja Eksploratora rozwiązań|Opis|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*hhp|*Projname*\hlp|pliki Pomocy w formacie HTML|Plik projektu pomocy. Zawiera ona dane potrzebne do skompilowania plików pomocy w postaci pliku .hxs lub plik chm.|
|*Projname*.hhk|*Projname*\hlp|pliki Pomocy w formacie HTML|Zawiera indeks tematów Pomocy.|
|*Projname*.hhc|*Projname*\hlp|pliki Pomocy w formacie HTML|Zawartość pomocy projektu.|
|Makehtmlhelp.bat|*Projname*|Pliki źródłowe|Używane przez system, aby skompilować projekt pomocy, gdy projekt jest skompilowany.|
|Afxcore.htm|*Projname*\hlp|Tematy Pomocy HTML|Zawiera standardowe tematy pomocy dla standardowych poleceń MFC i obiektów ekranu. Dodaj tematy pomocy do tego pliku.|
|Afxprint.htm|*Projname*\hlp|Tematy Pomocy HTML|Zawiera tematy pomocy dla polecenia drukowania.|
|\*.jpg; \*.gif|*Projname*\hlp\Images|Pliki zasobów|Zawiera obrazy do różnych tematów wygenerowany plik.|

## <a name="see-also"></a>Zobacz też

[Typy plików utworzonych dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)