---
title: 'CWinApp: Klasa aplikacji | Dokumentacja firmy Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CWinApp
dev_langs: C++
helpviewer_keywords:
- application class [MFC]
- CWinApp class [MFC], CWinThread
- MFC, WinMain and
- CWinApp class [MFC], multithreading
- CWinThread class [MFC], and CWinApp
- InitApplication method [MFC]
- WinMain method [MFC]
- WinMain method [MFC], in MFC
- CWinApp class [MFC], WinMain
ms.assetid: 935822bb-d463-481b-a5f6-9719d68ed1d5
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 46061c55bdf0bc8e6eb16a093fc8023c04939fa9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cwinapp-the-application-class"></a>CWinApp: klasa aplikacji
Klasy głównym aplikacji w MFC hermetyzuje inicjowania, uruchamianie i kończenie działania aplikacji dla systemu operacyjnego Windows. Aplikacji utworzonej w ramach musi mieć jeden i tylko jeden obiekt klasy pochodzące z [CWinApp](../mfc/reference/cwinapp-class.md). Ten obiekt jest tworzony, przed utworzeniem systemu windows.  
  
 `CWinApp`jest pochodną `CWinThread`, reprezentuje głównego wątku do wykonania dla aplikacji, co może mieć co najmniej jeden wątek. W nowszych wersjach MFC `InitInstance`, **Uruchom**, `ExitInstance`, i `OnIdle` funkcji elementów członkowskich są faktycznie klasy `CWinThread`. Te funkcje zostały omówione w tym miejscu tak, jakby były `CWinApp` elementów członkowskich, ponieważ Dyskusja dotyczy roli obiektu jako obiektu aplikacji, a nie jako podstawowy wątku.  
  
> [!NOTE]
>  Klasy aplikacji stanowi podstawowy wątku wykonywania aplikacji. Przy użyciu funkcji Win32 API, można również utworzyć dodatkowej wątków wykonywania. Biblioteki MFC można używać tych wątków. Aby uzyskać więcej informacji, zobacz [Multithreading](../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
 Podobnie jak dowolnego programu dla systemu operacyjnego Windows została aplikacji framework `WinMain` funkcji. W ramach aplikacji, jednak użytkownik nie zapisuj `WinMain`. Dostarczony przez biblioteki klas, a jest wywoływana podczas uruchamiania aplikacji. `WinMain`wykonuje standardowych usług takich jak rejestrowanie klas okien. Następnie wywołuje element członkowski funkcje obiektu aplikacji do zainicjowania i uruchomienia aplikacji. (Można dostosować `WinMain` przez zastąpienie `CWinApp` funkcje Członkowskie `WinMain` wywołań.)  
  
 Aby zainicjować aplikację, `WinMain` wywołania obiektu aplikacji `InitApplication` i `InitInstance` funkcji elementów członkowskich. Do uruchomienia aplikacji pętli komunikatów, `WinMain` wywołania **Uruchom** funkcję elementu członkowskiego. Na zakończenie `WinMain` wywołuje obiekt aplikacji `ExitInstance` funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Nazw wyświetlanych w **bold** w niniejszej dokumentacji wskazać elementów dostarczonych przez Microsoft Foundation Class Library i Visual C++. Nazw wyświetlanych w `monospaced` typu wskazuje elementy, które można tworzyć ani zastępować.  
  
## <a name="see-also"></a>Zobacz też  
 [Tematy ogólne dotyczące MFC](../mfc/general-mfc-topics.md)   
 [Klasa CWinApp i Kreator aplikacji MFC](../mfc/cwinapp-and-the-mfc-application-wizard.md)   
 [Funkcje Członkowskie CWinApp z możliwością zastąpienia](../mfc/overridable-cwinapp-member-functions.md)   
 [Specjalne usługi CWinApp](../mfc/special-cwinapp-services.md)

