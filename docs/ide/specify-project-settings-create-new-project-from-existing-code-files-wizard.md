---
title: "Określ ustawienia projektu Utwórz nowy projekt z istniejących Kreatora plików kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.importwiz.appsettings
dev_langs:
- C++
helpviewer_keywords:
- Create New Project From Existing Code Files Wizard, project settings
ms.assetid: 9b8860c9-d35f-4f18-9565-2934d3d7f569
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2cf1e8eba11063f7f2e46f836cd2ef84cc70dfe8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="specify-project-settings-create-new-project-from-existing-code-files-wizard"></a>Określ ustawienia projektu, Kreator Utwórz nowy projekt z istniejących plików z kodem
Umożliwia określenie tej strony kreator Utwórz nowy projekt z istniejących plików kodu:  
  
-   Środowisko kompilacji dla nowego projektu  
  
-   Ustawienia do dopasowania dla określonego typu nowy projekt, aby wygenerować kompilacji  
  
## <a name="task-list"></a>Lista zadań  
 [Instrukcje: tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md)  
  
## <a name="uielement-list"></a>Lista elementów UI  
 **Program Visual Studio**  
 Określa, aby użyć narzędzia kompilacji, które są uwzględniane w programie Visual Studio do tworzenia nowego projektu. Ta opcja jest domyślnie wybrana.  
  
 **Typ projektu**  
 Określa typ projektu, który zostanie wygenerowany przez kreatora.  
  
 **Projekt aplikacji systemu Windows**  
 Wskazuje, że kreator wygeneruje projekt wykonywalny aplikacji systemu Windows. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.  
  
 **Projekt aplikacji konsoli**  
 Wskazuje, że kreator wygeneruje projekt aplikacji konsoli. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.  
  
 **Połączone dynamicznie biblioteka (DLL) projektu**  
 Wskazuje, że kreator wygeneruje projekt aplikacji biblioteki dołączanej puste. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.  
  
 **Biblioteka statyczna (LIB) projektu**  
 Wskazuje, że kreator wygeneruje projekt aplikacji biblioteki statycznej. Ta opcja jest dostępna z **typu projektu** pole listy rozwijanej.  
  
 **Dodaj obsługę ATL**  
 Dodaje obsługę ATL do nowego projektu.  
  
 **Dodawanie obsługi MFC**  
 Dodaje obsługę MFC do nowego projektu.  
  
 **Dodaj obsługę środowisko uruchomieniowe języka wspólnego**  
 Dodaje CLR programowania pomocy technicznej do nowego projektu.  
  
 **Środowisko uruchomieniowe języka wspólnego**  
 Określa nowy projekt, aby było zgodne z funkcji CLR.  
  
 **Aparat plików wykonywalnych języka wspólnego (stara składnia)**  
 Określa nowy projekt, aby było zgodne z rozszerzeń zarządzanych dla składni języka C++, czyli CLR składni programowania przed Visual C++ 2005.  
  
 **Użyj zewnętrznego systemu do kompilacji**  
 Określa za pomocą narzędzi kompilacji, które nie znajdują się w programie Visual Studio do tworzenia nowego projektu. Gdy ta opcja jest zaznaczona, można określić wiersze poleceń kompilacji na **Określ ustawienia konfiguracji debugowania** i **Określ ustawienia konfiguracji wydania** stron.  
  
> [!NOTE]
>  Podczas **Użyj zewnętrznego systemu kompilacji** opcja jest zaznaczona, IDE nie kompiluje nowy projekt, więc /D, I, /FI, /AI lub /FU opcje nie są wymagane dla kompilacji. Jednak te opcje muszą być ustawione poprawnie Aby IntelliSense działać prawidłowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Określ ustawienia konfiguracji debugowania, Utwórz nowy projekt z istniejących Kreatora plików kodu](../ide/specify-debug-configuration-settings.md)   
 [Określanie ustawień konfiguracji wydania, Kreator Utwórz nowy projekt z istniejących plików z kodem](../ide/specify-release-configuration.md)