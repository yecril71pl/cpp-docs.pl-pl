---
title: Kreatorzy i edytory zasobów
ms.date: 11/04/2016
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
ms.openlocfilehash: fe55336d38393787988eac3a6f57394f3923260e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472751"
---
# <a name="wizards-and-the-resource-editors"></a>Kreatorzy i edytory zasobów

Visual C++ obejmuje kilka kreatorów do użytku w programowaniu MFC, wraz z wielu edytory zintegrowanych zasobów. Dla formantów ActiveX programowania, [kreatora kontrolek ActiveX](../mfc/reference/mfc-activex-control-wizard.md) pełni funkcję, podobnie jak w przypadku Kreator aplikacji MFC. Podczas pisania aplikacji MFC, bez większość tych narzędzi, narzędzia znacznie uprościć i przyspieszyć swoją pracę.

##  <a name="_core_use_appwizard_to_create_an_mfc_application"></a> Za pomocą Kreatora aplikacji MFC do tworzenia aplikacji MFC

Użyj [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) do utworzenia projektu MFC w programie Visual C++, może to być OLE i obsługa bazy danych. Pliki w projekcie zawierają aplikacji, dokumentu, widok i klasy okien ramowych; Standardowe zasoby, łącznie z menu i paska narzędzi opcjonalne; inne wymagane pliki Windows; i opcjonalnie .rtf — pliki zawierające standardowa tematy Pomocy Windows, które można skorygować i rozszerzyć, aby utworzyć plik Pomocy programu.

##  <a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a> Zarządzać klasy i komunikatów Windows za pomocą widoku klas

Klasy widoku ułatwia tworzenie funkcji obsługi dla Windows komunikaty i polecenia, tworzenie i zarządzanie klas, tworzenia zmiennych składowej klasy, tworzenie właściwości i metod automatyzacji, tworzenie klas baz danych i nie tylko.

> [!NOTE]
>  Widok klas pomaga też przesłonić funkcje wirtualne w klasach MFC. Wybierz klasy i funkcji wirtualnych do przesłonięcia. Pozostała część procesu jest podobny do obsługi komunikatów, zgodnie z opisem w sekcjach.

Aplikacje działające w środowisku Windows są [komunikat na podstawie](../mfc/message-handling-and-mapping.md). Akcje użytkownika i inne zdarzenia, które występują w uruchomiony program powodują Windows wysyłać komunikaty do systemu windows w programie. Na przykład jeśli użytkownik kliknie przycisk myszy w oknie, Windows wysyła wiadomości WM_LBUTTONDOWN po naciśnięciu lewego przycisku myszy, a komunikat WM_LBUTTONUP po zwolnieniu przycisku. Windows wysyła również wm_command — komunikaty, gdy użytkownik wybierze polecenia na pasku menu.

W ramach MFC różnych obiektów, takich jak dokumenty, widoki, okien ramowych, szablony dokumentów i obiekt aplikacji mogą "handle" wiadomości. Taki obiekt zawiera "Funkcja obsługi" jako jeden z jego elementów członkowskich funkcje i platformę mapy komunikatów przychodzących do jego obsługi.

Dużą część Twoim zadaniem jako programisty jest wybranie wiadomości, które można mapować na obiekty, które i następnie Implementowanie mapowania. Aby to zrobić, należy użyć widoku klas i oknie dialogowym właściwości.

W oknie właściwości utworzy funkcji elementów członkowskich pusty program obsługi komunikatów, a używasz Edytor kodu źródłowego do wdrożenia programu obsługi. Można również utworzyć lub edytować klasy (w tym klasy własny, nie pochodzi od klasy MFC) i ich członków, za pomocą widoku klas. Aby uzyskać więcej informacji na temat korzystania z widoku klas i kreatorzy dodawania kodu do projektu, zobacz [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md).

##  <a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a> Edytory zasobów umożliwia tworzenie i edytowanie zasobów

Używać Visual C++ [edytory zasobów](../windows/resource-editors.md) do tworzenia i edytowania menu, okna dialogowe, niestandardowe formanty, klawiszy skrótów, mapy bitowe, ikony, kursorów, ciągi i zasoby wersji. Począwszy od Visual C++ w wersji 4.0 Edytor paska narzędzi pasków narzędzi tworzenia bardzo ułatwia.

Aby pomóc Ci jeszcze więcej, biblioteki klas Microsoft Foundation udostępnia plik o nazwie wspólne. RES, który zawiera zasoby "clipart", które można skopiować z typowych. RES i Wklej w pliku zasobów. WSPÓLNE. RES zawiera przyciski paska narzędzi, typowe kursorów, ikony i inne. Można użyć, modyfikowania i rozpowszechniania tych zasobów w aplikacji. Aby uzyskać więcej informacji na temat typowych. RES, zobacz [przykładowe Clipart](../visual-cpp-samples.md).

Kreator aplikacji MFC, kreatorów Visual C++, edytory zasobów i struktura MFC sporego nakładu pracy dla siebie i należy kodu znacznie łatwiejsze zarządzanie. Duża część kodu aplikacji znajduje się w Twoich zajęciach dokument i widok.

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
