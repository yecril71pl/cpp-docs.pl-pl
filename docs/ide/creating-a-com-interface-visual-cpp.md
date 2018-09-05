---
title: Tworzenie interfejsu COM (Visual C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.com.creating.interfaces
dev_langs:
- C++
helpviewer_keywords:
- COM interfaces, creating
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c31dfc72e6d552cacd46f3e0b49aedc18bf4c7f2
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683316"
---
# <a name="creating-a-com-interface-visual-c"></a>Tworzenie interfejsu COM (Visual C++)
Visual C++ zapewnia kreatory i szablony do tworzenia projektów używających definiowanie interfejsów COM i dispinterfaces dla obiektów COM i klasy automatyzacji.  
  
 Te kreatory służy do wykonywania następujących trzech typowych zadań:  
  
-   [Dodawanie obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md)  
  
     Dodaj obsługę ATL do aplikacji MFC, po utworzeniu projektu MFC przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) , a następnie uruchamiając **Dodawanie obsługi ATL do MFC** kreatora kodów. Ta funkcja dotyczy tylko proste obiekty COM, dodane do projektu biblioteki DLL lub pliku wykonywalnego MFC. Te obiekty ATL może mieć wiele interfejsów.  
  
-   [Tworzenie kontrolki ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md)  
  
     Otwórz [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) tworzenia kontrolki ActiveX z dispinterface i mapę zdarzeń zdefiniowanych w pliku .idl i klasy kontrolek, odpowiednio.  
  
-   [Dodawanie kontrolki ATL](../atl/reference/adding-an-atl-control.md)  
  
     Użyj kombinacji [Kreator projektów ATL](../atl/reference/atl-project-wizard.md) i [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md) do tworzenia formantu ATL ActiveX.  
  
     Można również dodać kontrolki ATL do projektu MFC, do której dodano obsługę ATL, zgodnie z powyższym opisem. Ponadto jeśli zostanie wybrana **kontrolka ATL** w **Dodaj klasę** okno dialogowe, a nie zostały jeszcze dodane obsługi ATL do projektu MFC, Visual Studio wyświetli okno dialogowe potwierdzające Dodawanie obsługi ATL do usługi Projekt MFC.  
  
     Ten kreator generuje źródło IDL i mapy COM w klasach projektu.  
  
 Po utworzeniu projektu ATL otworzyć, [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe umożliwia wybór dodatkowe kreatorów i szablonów, aby dodać interfejsy modelu COM do projektu. Zezwalaj na następujących kreatorów, ustanowienia co najmniej jeden interfejs dla obiektu:  
  
-   [Kreator składników ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)  
  
-   [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)  
  
-   [Kreator składników stron Active Server Page ATL](../atl/reference/atl-active-server-page-component-wizard.md)  
  
-   [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)  
  
 Ponadto można wdrożyć nowe interfejsy na kontrolki COM, klikając prawym przyciskiem myszy obiekt klasy formantu w widoku klas i klikając [implementować interfejs](../ide/implement-interface-wizard.md).  
  
> [!NOTE]
>  Program Visual Studio nie udostępnia kreatora, aby dodać interfejs do projektu. Można dodać interfejs do projektu ATL lub do [Dodawanie obsługi ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodanie przy użyciu prostego obiektu [proste Kreator obiektu ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz pliku .idl projektu i Utwórz interfejs, wpisując:  
  
```  
interface IMyInterface {  
};  
  
```  
  
 Zobacz [implementującej interfejs](../ide/implementing-an-interface-visual-cpp.md) i [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Aby uzyskać więcej informacji.  
  
 Visual C++ oferuje kilka sposobów, aby wyświetlić i [Edytuj interfejsów COM](../ide/editing-a-com-interface.md) zdefiniowane dla Twoich projektów. [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) Wyświetla ikony dla dowolnej interfejsu dispinterface zdefiniowane w pliku .idl w projekcie języka C++.  
  
 Dla klas obiektów oparty na bibliotece ATL COM widoku klasy odczytuje mapy COM w klasy ATL do wyświetlania relacji między klasą ATL i wszystkie interfejsy, które implementuje.  
  
 W widoku klas i jego menu skrótów można pracować z interfejsów w następujący sposób:  
  
-   Dodaj obiekty ATL z aplikacją oparty na bibliotece MFC.  
  
-   Dodaj metody, właściwości i zdarzenia.  
  
-   Przechodzić bezpośrednio do elementu kod interfejsu, klikając ten element.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie projektów pulpitu za pomocą kreatorów aplikacji](../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md)