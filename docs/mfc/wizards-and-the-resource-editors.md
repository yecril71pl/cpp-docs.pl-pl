---
title: "Kreatorzy i edytory zasobów | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application wizards [MFC], and MFC
- MFC, resource editors
- resource editors, MFC
- MFC Application Wizard
- editors [MFC], resource
- wizards [MFC]
- wizards [MFC], MFC programming
- MFC, wizards
- Class View tool, managing Windows messages
ms.assetid: f5dd4d13-9dc1-4a49-b6bf-5b3cb45fa8ba
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c91ba5c74ebda12df4bc912ac8bd760263364345
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="wizards-and-the-resource-editors"></a>Kreatorzy i edytory zasobów
Visual C++ obejmuje kilka kreatorów do użycia w programowaniu MFC, oraz wiele edytorów zintegrowanym. Dla formantów ActiveX programowania, [Kreator kontrolek ActiveX](../mfc/reference/mfc-activex-control-wizard.md) pełni funkcję, podobne jak w przypadku Kreator aplikacji MFC. Podczas pisania aplikacji MFC bez większość tych narzędzi, narzędzia znacznie uprościć i przyspieszyć pracę.  
  
##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a>Kreator aplikacji MFC umożliwia tworzenie aplikacji MFC  
 Użyj [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) do tworzenia projektu MFC w programie Visual C++, która może obejmować OLE i obsługa bazy danych. Pliki w projekcie zawierają aplikacji, dokumentu, widok i klasy okien ramowych; Standardowe zasoby, w tym menu i paska narzędzi opcjonalne; inne wymagane pliki systemu Windows; i opcjonalnie .rtf — pliki zawierające standardowe tematy Pomocy systemu Windows, które można skorygować i rozszerzyć, aby utworzyć plik Pomocy programu.  
  
##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Zarządzanie klas i komunikatów systemu Windows za pomocą klasy widoku  
 Klasa widok pomaga utworzyć funkcje obsługi komunikatów systemu Windows i poleceń, Utwórz i Zarządzaj klasy, Utwórz element członkowski klasy zmienne, utworzyć automatyzacji metody i właściwości, Tworzenie klasy baz danych i inne.  
  
> [!NOTE]
>  Widok klasy pomaga również przesłonić funkcje wirtualne klas MFC. Wybierz klasę i funkcji wirtualnych do przesłonięcia. Pozostała część procesu jest podobny do obsługi wiadomości, zgodnie z opisem w poniższych punktach.  
  
 Aplikacje działające w systemie Windows są [komunikat zmiennych](../mfc/message-handling-and-mapping.md). Akcje użytkownika oraz inne zdarzenia, które występują w uruchomiony program spowodować systemu Windows do wysyłania komunikatów do systemu windows w programie. Na przykład, jeśli użytkownik kliknie przycisk myszy w oknie, system Windows wysyła `WM_LBUTTONDOWN` po naciśnięciu lewego przycisku myszy i a komunikatów `WM_LBUTTONUP` komunikatu po zwolnieniu przycisku. System Windows wysyła również **WM_COMMAND** wiadomości, gdy użytkownik wybierze polecenia na pasku menu.  
  
 W ramach MFC różnych obiektów, takich jak dokumenty, widoki, okien ramowych, szablony dokumentów i obiekt aplikacji może "obsługiwać" wiadomości. Taki obiekt zapewnia "Funkcja obsługi" jako jeden z jego elementów członkowskich funkcje i platformę mapy komunikatów przychodzących do jego obsługi.  
  
 Dużą część zadania programowania jest wybranie wiadomości, które można mapować na obiekty, które i następnie Implementowanie mapowania. Aby to zrobić, użyj widoku klasy i w oknie właściwości.  
  
 Okno właściwości utworzy funkcji Członkowskich pusty obsługi wiadomości i obsługi wdrożenia za pomocą edytora kodu źródła. Można utworzyć lub edytować klasy (w tym klasy własny nie pochodzi od klasy MFC) i ich elementy członkowskie z widoku klasy. Aby uzyskać więcej informacji na widoku klasy i kreatorów, które Dodawanie kodu do projektu, zobacz [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md).  
  
##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Edytory zasobów umożliwia tworzenie i edytowanie zasobów  
 Użyj Visual C++ [edytory zasobów](../windows/resource-editors.md) można tworzyć i edytować menu, okien dialogowych, niestandardowych formantów, klawisze skrótów, mapy bitowe, ikony, kursorów, ciągi i zasoby wersji. Począwszy od programu Visual C++ w wersji 4.0 Edytor paska narzędzi ułatwia utworzenie pasków narzędzi znacznie.  
  
 Aby pomóc Ci jeszcze więcej, Microsoft Foundation Class Library zawiera plik o nazwie wspólnej. RES, zawierającą zasoby "klip grafik", które można skopiować z typowych. RES i Wklej do pliku zasobów. TYPOWE. RES zawiera przyciski paska narzędzi, typowe kursory, ikony i inne. Można użyć, modyfikowania i Ponowna dystrybucja tych zasobów w aplikacji. Aby uzyskać więcej informacji na temat wspólnego. RES, zobacz [próbki Clipart](../visual-cpp-samples.md).  
  
 Kreator aplikacji MFC, kreatorów Visual C++, edytory zasobów i struktura MFC jak dużo pracy i kod znacznie łatwiejsze zarządzanie. Zbiorczego kodu określonych aplikacji znajduje się w dokumencie i widoku klas.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
