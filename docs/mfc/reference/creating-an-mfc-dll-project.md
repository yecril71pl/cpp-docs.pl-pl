---
title: Tworzenie projektu MFC DLL | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfcdll.project
dev_langs:
- C++
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a7c040188db5caf46c0d58720320088967b59ea6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-mfc-dll-project"></a>Tworzenie projektu MFC DLL
Biblioteki MFC DLL jest plikiem binarnym, który działa jako biblioteki udostępnionej funkcji, które mogą być używane równocześnie przez wiele aplikacji. Najprostszym sposobem tworzenia projektu MFC DLL jest za pomocą Kreatora biblioteki DLL MFC.  
  
> [!NOTE]
>  Wygląd funkcji w środowisku IDE może zależeć od wersji lub aktywne ustawienia i może się różnić od opisanych w Pomocy. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>Aby utworzyć projekt MFC DLL przy użyciu Kreatora biblioteki DLL MFC  
  
1.  Postępuj zgodnie z instrukcjami w temacie Pomocy [Tworzenie projektu za pomocą Kreatora aplikacji Visual C++](../../ide/creating-desktop-projects-by-using-application-wizards.md).  
  
 **Uwaga** w **nowy projekt** okno dialogowe, wybierz opcję `MFC DLL` ikonę w okienku szablonów, aby otworzyć Kreatora biblioteki DLL MFC.  
  
1.  Definiowanie ustawień aplikacji za pomocą [ustawienia aplikacji](../../mfc/reference/application-settings-mfc-dll-wizard.md) strony [Kreator biblioteki DLL MFC](../../mfc/reference/mfc-dll-wizard.md).  
  
    > [!NOTE]
    >  Pomiń ten krok, aby kreator ustawienia domyślne.  
  
2.  Kliknij przycisk **Zakończ** aby zamknąć kreatora i otworzyć nowego projektu w **Eksploratora rozwiązań**.  
  
 Po utworzeniu projektu można wyświetlić plików utworzonych w Eksploratorze rozwiązań. Aby uzyskać więcej informacji o plikach Kreator tworzy dla projektu można znaleźć w pliku wygenerowanego projektu ReadMe.txt. Aby uzyskać więcej informacji na temat typów plików, zobacz [pliku typy utworzone dla projektów Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy projektów Visual C++](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)   
 [Dodawanie funkcji z kreatorami kodów](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Strony właściwości](../../ide/property-pages-visual-cpp.md)   
 [Wdrażanie aplikacji](http://msdn.microsoft.com/en-us/4ff8881d-0daf-47e7-bfe7-774c625031b4)

