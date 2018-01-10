---
title: Tworzenie interfejsu COM (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.com.creating.interfaces
dev_langs: C++
helpviewer_keywords: COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e7b5820686c3e6f01c37cbf527d0e631e5bcc25c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-com-interface-visual-c"></a>Tworzenie interfejsu COM (Visual C++)
Visual C++ udostępnia kreatorów i szablony do tworzenia projektów używające definiującego interfejsy modelu COM i dispinterfaces dla obiektów COM i klas automatyzacji.  
  
 Tych kreatorów umożliwia wykonywanie następujących trzech typowych zadań:  
  
-   [Dodawanie obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     Dodaj obsługę ATL do MFC aplikacji po utworzeniu projektu MFC przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) , a następnie uruchamiając **Dodawanie obsługi ATL do MFC** kodu kreatora. Ta obsługa dotyczy tylko prostych obiektów COM dodane do pliku wykonywalnego MFC lub projektu biblioteki DLL. Te obiekty ATL może mieć wiele interfejsów.  
  
-   [Tworzenie kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     Otwórz [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) można utworzyć formantu ActiveX dispinterface i mapę zdarzeń zdefiniowanych w pliku .idl i klasy formantu odpowiednio.  
  
-   [Dodawanie kontrolki ATL](../atl/reference/adding-an-atl-control.md)  
  
     Użyj kombinacji [Kreator projektu ATL](../atl/reference/atl-project-wizard.md) i [Kreator formantu ATL](../atl/reference/atl-control-wizard.md) można utworzyć formantu ATL ActiveX.  
  
     Można również dodać formantu ATL do projektu MFC, do której dodano obsługę ATL, zgodnie z powyższym opisem. Ponadto w przypadku wybrania **formantu ATL** w **Dodaj klasę** okno dialogowe, a nie zostały jeszcze dodane obsługi ATL do projektu MFC, Visual Studio Wyświetla okno dialogowe Dodawanie obsługi ATL do potwierdzenia Twojej Projekt MFC.  
  
     Ten kreator generuje źródło IDL i mapowanie modelu COM w klasach projektu.  
  
 Po utworzeniu otwarcia, Projekt ATL [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe umożliwia wybór dodatkowe kreatorów i szablony, aby dodać interfejsy modelu COM do projektu. Następujących kreatorów pozwalają na wprowadzenie co najmniej jeden interfejs dla obiektu:  
  
-   [Kreator składników ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)  
  
-   [Kreator składników stron Active Server Page ATL](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)  
  
 Ponadto można wdrożyć nowe interfejsy COM formantu prawym przyciskiem myszy obiekt klasy formantu w widoku klas, a następnie klikając polecenie [implementować interfejs](../ide/implement-interface-wizard.md).  
  
> [!NOTE]
>  Program Visual Studio nie udostępnia kreatora, aby dodać interfejs do projektu. Można dodać interfejs do Projekt ATL lub do [Dodawanie obsługi ATL do projektu MFC Your](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodawanie przy użyciu prostego obiektu [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz pliku .idl projektu i utworzyć interfejsu, wpisz:  
  
```  
interface IMyInterface {  
};  
  
```  
  
 Zobacz [implementującej interfejs](../ide/implementing-an-interface-visual-cpp.md) i [Dodawanie obiektów i kontroli w celu Projekt ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Aby uzyskać więcej informacji.  
  
 Visual C++ udostępnia kilka sposobów, aby wyświetlić i [Edytuj interfejsy modelu COM](../ide/editing-a-com-interface.md) zdefiniowane dla projektów. [Widok klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) Wyświetla ikony dla interfejsu lub dispinterface zdefiniowane w pliku .idl w projekcie języka C++.  
  
 Dla klas obiektów oparty na ATL COM widoku klasy odczytuje mapie modelu COM klasy ATL do wyświetlenia relacji między klasą ATL i wszystkie interfejsy, które implementuje.  
  
 W widoku klas i jego menu skrótów możesz pracować z interfejsów w następujący sposób:  
  
-   Dodawanie obiektów ATL do aplikacji opartych na MFC.  
  
-   Dodaj metody, właściwości i zdarzeń.  
  
-   Przejście bezpośrednio w kodzie interfejsu elementu, klikając ten element.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md)