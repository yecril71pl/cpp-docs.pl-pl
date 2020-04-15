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
ms.openlocfilehash: 04d9f2cf615636b151af93a3c3880f7357496048
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365274"
---
# <a name="wizards-and-the-resource-editors"></a>Kreatorzy i edytory zasobów

Visual C++ zawiera kilka kreatorów do użycia w programowaniu MFC, wraz z wielu zintegrowanych edytorów zasobów. W przypadku programowania formantów ActiveX [Kreator kontroli ActiveX](../mfc/reference/mfc-activex-control-wizard.md) służy celowi podobne do celu Kreatora aplikacji MFC. Chociaż można pisać aplikacje MFC bez większości z tych narzędzi, narzędzia znacznie upraszczają i przyspieszają pracę.

## <a name="use-the-mfc-application-wizard-to-create-an-mfc-application"></a><a name="_core_use_appwizard_to_create_an_mfc_application"></a>Tworzenie aplikacji MFC za pomocą Kreatora aplikacji MFC

Użyj [Kreatora aplikacji MFC,](../mfc/reference/mfc-application-wizard.md) aby utworzyć projekt MFC w języku Visual C++, który może zawierać obsługę OLE i bazy danych. Pliki w projekcie zawierają klasy aplikacji, dokumentu, widoku i okna ramki; standardowe zasoby, w tym menu i opcjonalny pasek narzędzi; inne wymagane pliki systemu Windows; oraz opcjonalne pliki rtf zawierające standardowe tematy Pomocy systemu Windows, które można poprawić i rozszerzyć, aby utworzyć plik pomocy programu.

## <a name="use-class-view-to-manage-classes-and-windows-messages"></a><a name="_core_use_classwizard_to_manage_classes_and_windows_messages"></a>Używanie widoku klasy do zarządzania klasami i wiadomościami systemu Windows

Widok klasy ułatwia tworzenie funkcji obsługi dla komunikatów i poleceń systemu Windows, tworzenie klas i zarządzanie nimi, tworzenie zmiennych elementów członkowskich klasy, tworzenie metod i właściwości automatyzacji, tworzenie klas bazy danych i inne.

> [!NOTE]
> Widok klasy pomaga również zastąpić funkcje wirtualne w klasach MFC. Wybierz klasę i funkcję wirtualną do zastąpienia. Pozostała część procesu jest podobna do obsługi wiadomości, jak opisano w poniższych akapitach.

Aplikacje działające w systemie Windows są [sterowane komunikatami](../mfc/message-handling-and-mapping.md). Akcje użytkownika i inne zdarzenia występujące w uruchomionym programie powodują, że system Windows wysyła wiadomości do okien w programie. Na przykład jeśli użytkownik kliknie myszą w oknie, system Windows wyśle komunikat WM_LBUTTONDOWN po naciśnięciu lewego przycisku myszy i WM_LBUTTONUP komunikat po zwolnieniu przycisku. System Windows wysyła również WM_COMMAND wiadomości, gdy użytkownik wybiera polecenia z paska menu.

W ramach MFC różne obiekty, takie jak dokumenty, widoki, okna ramek, szablony dokumentów i obiekt aplikacji, mogą "obsługiwać" wiadomości. Taki obiekt udostępnia "funkcję obsługi" jako jedną z jego funkcji członkowskich, a struktura mapuje przychodzącą wiadomość do jego programu obsługi.

Duża część zadania programowania jest wybór komunikatów do mapowania do których obiektów, a następnie zaimplementowanie tego mapowania. W tym celu należy użyć widoku klasy i [Kreatora zajęć](reference/mfc-class-wizard.md).

[Kreator klasy](reference/mfc-class-wizard.md) utworzy funkcje członkowskie pustych wiadomości obsługi wiadomości i użyjesz edytora kodu źródłowego do zaimplementowania treści programu obsługi. Można również tworzyć lub edytować klasy (w tym własne klasy, nie pochodzące z klas MFC) i ich członków z widoku klasy. Aby uzyskać więcej informacji na temat korzystania z widoku klasy i kreatorów, którzy dodają kod do projektu, zobacz [Dodawanie funkcji za pomocą Kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md).

## <a name="use-the-resource-editors-to-create-and-edit-resources"></a><a name="_core_use_the_resource_editors_to_create_and_edit_resources"></a>Tworzenie i edytowanie zasobów za pomocą edytorów zasobów

[Edytory zasobów](../windows/resource-editors.md) visual c++ umożliwia tworzenie i edytowanie menu, okien dialogowych, formantów niestandardowych, klawiszy akceleratora, map bitowych, ikon, kursorów, ciągów i zasobów wersji. Od wersji Visual C++ 4.0 edytor paska narzędzi znacznie ułatwia tworzenie pasków narzędzi.

Aby jeszcze bardziej pomóc, biblioteka klas programu Microsoft Foundation udostępnia plik o nazwie COMMON. OZE, który zawiera zasoby "clipart", które można skopiować z COMMON. OZE i wklej do własnego pliku zasobów. Wspólne. OZE zawiera przyciski paska narzędzi, typowe kursory, ikony i inne. Można użyć, zmodyfikować i rozpowszechniać te zasoby w aplikacji. Aby uzyskać więcej informacji na temat COMMON. res, zobacz [przykład Clipart](../overview/visual-cpp-samples.md).

Kreator aplikacji MFC, kreatorzy języka Visual C++, edytory zasobów i struktura MFC wykonują wiele pracy i znacznie ułatwiają zarządzanie kodem. Większość kodu specyficznego dla aplikacji znajduje się w klasie dokumentu i widoku.

## <a name="see-also"></a>Zobacz też

[Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md)
