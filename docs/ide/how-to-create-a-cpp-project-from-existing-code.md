---
title: 'Porady: Tworzenie projektu C++ z istniejącego kodu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++, creating projects from existing code
ms.assetid: e328a938-395c-48ea-9e35-dd433de12b31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1786e5704d7afd07576ab738d907eb841518f8be
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33330138"
---
# <a name="how-to-create-a-c-project-from-existing-code"></a>Porady: tworzenie projektu C++ z istniejącego kodu

W programie Visual Studio może portu do istniejących plików kodu do projektu Visual C++ przy użyciu **Utwórz nowy projekt z istniejących plików kodu** kreatora. Ten kreator nie jest dostępne w starszych wersjach Express programu Visual Studio. Ten kreator tworzy nowe rozwiązanie i projekt, który korzysta z systemu MSBuild do zarządzania plikami źródłowymi systemu i konfiguracja kompilacji.  
  
Przenoszenie istniejących plików kodu do projektu Visual C++ pozwala korzystać ze wszystkich funkcji zarządzania natywnego projektu MSBuild wbudowanych w IDE. Jeśli wolisz korzystać z istniejącego systemu kompilacji, takie jak pliki reguł programu make nmake, CMake lub rozwiązań alternatywnych, można użyć opcji Otwórz Folder. Aby uzyskać więcej informacji, zobacz [Otwórz Folder projekty w programie Visual C++](../ide/non-msbuild-projects.md). Obie te opcje umożliwiają używanie IDE funkcje takie jak [IntelliSense](/visualstudio/ide/using-intellisense) i [właściwości projektu](../ide/working-with-project-properties.md).  
  
### <a name="to-create-a-c-project-from-existing-code"></a>Aby utworzyć projekt C++ z istniejącego kodu  
  
1.  Na **pliku** menu wskaż **nowy**, a następnie kliknij przycisk **projektu z istniejącego kodu**.  
  
1.  Na pierwszej stronie **Utwórz nowy projekt z istniejących plików kodu** kreatora wybierz **Visual C++** w **jaki typ projektu chcesz utworzyć** listy. Wybierz **dalej** aby kontynuować. 
  
1.  Określanie lokalizacji projektu i katalog dla plików źródłowych. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ lokalizację projektu i plików źródłowych, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-project-location-and-source-files.md). Wybierz **dalej** aby kontynuować.  
  
1.  Określ ustawienia projektu do użycia. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ ustawienia projektu, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md). Wybierz **dalej** aby kontynuować.  

1.  Określ ustawienia konfiguracji debugowania do użycia. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ ustawienia konfiguracji debugowania, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-debug-configuration-settings.md). Wybierz **dalej** aby kontynuować.  

1.  Określ ustawienia konfiguracji wydania do użycia. Aby uzyskać więcej informacji na tej stronie, zobacz [Określ ustawienia konfiguracji wydania, utworzyć Kreator nowego projektu z istniejącego kodu pliki](../ide/specify-release-configuration.md). Wybierz **Zakończ** aby wygenerować nowy projekt.  
  
## <a name="see-also"></a>Zobacz też  

[Określ projektu lokalizacji i plików źródłowych, Utwórz nowy projekt z istniejących Kreatora plików kodu](../ide/specify-project-location-and-source-files.md)   
[Określ ustawienia projektu, Utwórz nowy projekt z istniejących Kreatora plików kodu](../ide/specify-project-settings-create-new-project-from-existing-code-files-wizard.md)   
[Określ ustawienia konfiguracji debugowania, Utwórz nowy projekt z istniejących Kreatora plików kodu](../ide/specify-debug-configuration-settings.md)   
[Określanie ustawień konfiguracji wydania, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-release-configuration.md)