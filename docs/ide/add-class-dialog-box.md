---
title: Okno dialogowe Dodaj klasę | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.addclass
dev_langs:
- C++
helpviewer_keywords:
- Add Class dialog box
ms.assetid: 916259b8-8e5f-4267-bd10-313483beba67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f6c4f108b30babcc30ffc5f2fc4c63fe764db2e3
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "33339777"
---
# <a name="add-class-dialog-box"></a>Okno dialogowe Dodaj klasę
**Dodaj klasę** okno dialogowe zawiera szablony, które umożliwiają:  
  
-   Otwórz odpowiedniego kreatora kodu, jeśli jest dostępny. Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
 \- lub -  
  
-   Automatyczne tworzenie nowej klasy, dodając odpowiednie pliki i kod źródłowy do projektu.  
  
 Dostęp można uzyskać **Dodaj klasę** okno dialogowe z **projektu** menu **Eksploratora rozwiązań**, lub [widoku klasy](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
> [!NOTE]
>  Gdy użytkownik spróbuje dodać klasę, która nie jest przeznaczone do bieżącego projektu, otrzymasz komunikat o błędzie. Kliknij przycisk **OK** aby powrócić do **Dodaj klasę** okno dialogowe.  
  
## <a name="add-class-templates"></a>Dodaj szablony klas  
 Istnieją cztery kategorie **Dodaj klasę** szablony: .NET, ATL MFC i rodzajowy. Po wybraniu szablonu w **szablony** okienku tekst opisujący wybór będą wyświetlane w obszarze **kategorii** i **szablony** okienka.  
  
### <a name="net"></a>.NET  
  
|Szablon|Kreator|  
|--------------|------------|  
|Usługa sieci Web ASP.NET|Niedostępne|  
|Klasa składnika (.NET)|Niedostępne|  
|Instalator klasy (.NET)|Niedostępne|  
|Kontrolki użytkownika (.NET)|Niedostępne|  
|Formularz systemu Windows (.NET)|Niedostępne|  
  
### <a name="atl"></a>ATL  
  
|Szablon|Kreator|  
|--------------|------------|  
|Dodaj obsługę ATL do MFC|Niedostępne|  
|Składnik strony Active Server ATL|[Kreator składników stron Active Server Page ATL](../atl/reference/atl-active-server-page-component-wizard.md)|  
|Formant ATL|[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)|  
|Okno dialogowe ATL|[Kreator okna dialogowego ATL](../atl/reference/atl-dialog-wizard.md)|  
|Składnik ATL COM + 1.0|[Kreator składników ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)|  
|Konsument OLE DB ATL|[Kreator konsumenta OLE DB ATL](../atl/reference/atl-ole-db-consumer-wizard.md)|  
|Dostawca OLE DB ATL|[Kreator dostawcy interfejsu OLE DB ATL](../atl/reference/atl-ole-db-provider-wizard.md)|  
|Strony właściwości ATL|[Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md)|  
|Prosty obiekt ATL|[Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)|  
|Dostawcy zdarzeń WMI|Kreator dostawcy zdarzeń WMI|  
|Dostawca WMI wystąpienia|Kreator dostawcy wystąpienia usługi WMI|  
  
### <a name="mfc"></a>MFC  
  
|Szablon|Kreator|  
|--------------|------------|  
|Klasa MFC|[Kreator dodawania klasy MFC](../mfc/reference/mfc-add-class-wizard.md)|  
|Klasa MFC z formantu ActiveX|[Kreator dodawania klasy z kontrolki ActiveX](../ide/add-class-from-activex-control-wizard.md)|  
|Klasa MFC z biblioteki typów|[Biblioteki typów Kreator dodawania klasy z](../mfc/reference/add-class-from-typelib-wizard.md)|  
|Konsumenta MFC ODBC|[Kreator użytkownika MFC ODBC](../mfc/reference/mfc-odbc-consumer-wizard.md)|  
  
### <a name="generic-classes"></a>Klasy ogólne  
  
|Szablon|Kreator|  
|--------------|------------|  
|Klasy generycznej C++|[Kreator rodzajowej klasy C++](../ide/generic-cpp-class-wizard.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)   
 [Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)   
 [Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)