---
title: "Tworzenie projektu pliku reguł programu make | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.makefile.project
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, creating
- project files [C++], Makefile projects
ms.assetid: dd077af3-97a8-48fb-baaa-cf7e07ddef61
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5e86bedbf83cd417cfc41317e5887304cda7ee76
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-makefile-project"></a>Tworzenie projektu pliku reguł programu make
Jeśli masz projekt, który kompilujesz z wiersza polecenia za pomocą pliku makefile, środowisko programistyczne Visual Studio nie rozpozna projektu. Aby otworzyć i kompilacji, Twój projekt używający [!INCLUDE[vsUltShort](../ide/includes/vsultshort_md.md)], Visual Studio Professional i Visual Studio Express for Windows Desktop, wybierając szablon projektu pliku reguł programu make najpierw utworzyć pusty projekt. Następnie użyj tego projektu do stworzenia własnego projektu w środowisku programistycznym Visual Studio.  
  
 Projekt nie wyświetla żadnych plików w Eksploratorze rozwiązań. Projekt określa ustawienia kompilacji, które są odzwierciedlane na stronie właściwości projektu.  
  
 Plik wyjściowy określany w projekcie nie ma wpływu na nazwę, którą generuje skrypt kompilacji; deklaruje tylko zamiar.  
  
### <a name="to-create-a-makefile-project"></a>Aby utworzyć projekt Makefile  
  
1.  Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu za pomocą Kreatora aplikacji Visual C++](../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
2.  W **nowy projekt** okno dialogowe, wybierz opcję **projektu pliku reguł programu make** w okienku szablonów, aby otworzyć kreatora.  
  
3.  W [ustawienia aplikacji](../ide/application-settings-makefile-project-wizard.md) strony, podaj polecenie output, czyszczenia i Odbuduj informacji.  
  
4.  Kliknij przycisk **Zakończ** aby zamknąć kreatora i otwórz nowo utworzony projekt w **Eksploratora rozwiązań**.  
  
 Możesz przeglądać i modyfikować właściwości projektu na stronie właściwości. Zobacz [Ustawianie właściwości projektu Visual C++](../ide/working-with-project-properties.md) informacje dotyczące wyświetlania strony właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator projektu pliku reguł programu make](../ide/makefile-project-wizard.md)   
 [Znaki specjalne w pliku reguł programu make](../build/special-characters-in-a-makefile.md)   
 [Zawartość pliku reguł programu Make](../build/contents-of-a-makefile.md)