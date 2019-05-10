---
title: Dodaj klasę
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.classes.adding
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: 4cd4ed4d4ec5a7093ce674c7883a77fa4e91d5ef
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446936"
---
# <a name="add-a-class"></a>Dodaj klasę

Aby dodać klasę w programie Visual Studio C++ projektu w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt, wybierz pozycję **Dodaj**, a następnie wybierz **klasy**. Spowoduje to otwarcie [okno dialogowe Dodaj klasę](#add-class-dialog-box).

Po dodaniu klasy, należy określić nazwę, która różni się od klas, które już istnieją w MFC ani ATL. Jeśli określisz nazwę, która już istnieje w jednej bibliotece IDE Wyświetla informację o błędzie.

Jeśli projekt konwencji nazewnictwa wymaga użycia istniejącej nazwy, możesz po prostu zmienić wielkość liter w co najmniej jedną literę w polu Nazwa ponieważ C++ jest uwzględniana wielkość liter. Na przykład mimo że nie można nadać nazwy klasy `CDocument`, nadaj jej nazwę `cdocument`.

## <a name="in-this-section"></a>W tej sekcji

- [Jakiego rodzaju klasy chcesz dodać?](#what-kind-of-class-do-you-want-to-add)
- [Okno dialogowe Dodawanie klasy](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>Jakiego rodzaju klasy chcesz dodać?

W **Dodaj klasę** okno dialogowe, po rozwinięciu **Visual C++** węzła w okienku po lewej stronie, wyświetlanych jest kilka grup zainstalowanych szablonów. Są to **CLR**, **ATL**, **MFC**, i **C++**. Po wybraniu grupy, listę dostępnych szablonów w tej grupie jest wyświetlane w środkowym okienku. Każdy szablon zawiera pliki i kod źródłowy, które są wymagane dla klasy.

Aby wygenerować nową klasę, w środkowym okienku wybierz szablon, wpisz nazwę dla klasy w **nazwa** i zaznacz **Dodaj**. Spowoduje to otwarcie **Kreator dodawania klasy** tak, aby określić opcje dla tej klasy.

- Aby uzyskać więcej informacji na temat sposobu tworzenia klas MFC, zobacz [klasy MFC](../mfc/reference/adding-an-mfc-class.md).

- Aby uzyskać więcej informacji na temat tworzenia klasy ATL, zobacz [prosty obiekt ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
> Szablon **Dodawanie obsługi ATL do MFC** nie tworzy klasę, ale zamiast tego konfiguruje projekt, aby użyć ATL. Aby uzyskać więcej informacji, zobacz [ATL pomocy technicznej w projekcie MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Aby klasy języka C++, która nie używa MFC, ATL lub CLR, użyj **klasy języka C++** szablonu w **C++** grupy zainstalowanych szablonów. Aby uzyskać więcej informacji, zobacz [Dodawanie rodzajowej klasy C++](../ide/adding-a-generic-cpp-class.md).

Dostępne są dwa rodzaje klas C++ opartych na formularzach. Pierwsza z nich, [klasa CFormView](../mfc/reference/cformview-class.md), tworzy klasę MFC. Drugi tworzy klasę CLR Windows Forms.

## <a name="add-class-dialog-box"></a>Dodaj klasę — Okno dialogowe

**Dodaj klasę** okno dialogowe zawiera szablony, które pozwalają na:

- Otwórz odpowiedniego kreatora kodów, jeśli jest dostępny. Aby uzyskać więcej informacji, zobacz [dodają funkcje za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- lub —

- Automatycznie Utwórz nowej klasy, dodając odpowiednie pliki i kod źródłowy do projektu.

Możesz uzyskać dostęp **Dodaj klasę** okno dialogowe z **projektu** menu **Eksploratora rozwiązań**, lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Gdy spróbujesz dodać klasę, która nie jest przeznaczone do bieżącego projektu, otrzymasz komunikat o błędzie. Wybierz **OK** aby powrócić do **Dodaj klasę** okno dialogowe.

### <a name="add-class-templates"></a>Dodawanie szablonów klas

Istnieją cztery kategorie **Dodaj klasę** szablonów: .NET, ATL, MFC i ogólnych. Po wybraniu szablonu w **szablony** okienku tekst opisujący wybór pojawi się w obszarze **kategorie** i **szablony** okienka.

#### <a name="net"></a>.NET

|Szablon|Kreator|
|--------------|------------|
|ASP.NET Web Service|Niedostępne|
|Klasa składników (.NET)|Niedostępne|
|Klasa Instalatora (.NET)|Niedostępne|
|Kontrolka użytkownika (.NET)|Niedostępne|
|Formularz Windows (.NET)|Niedostępne|

#### <a name="atl"></a>ATL

|Szablon|Kreator|
|--------------|------------|
|Dodaj obsługę ATL do MFC|Niedostępne|
|Składnika strony Active Server ATL|[Kreator składników stron active server ATL](../atl/reference/atl-active-server-page-component-wizard.md)|
|Kontrolka ATL|[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)|
|Okno dialogowe ATL|[Kreator okna dialogowego ATL](../atl/reference/atl-dialog-wizard.md)|
|Składnik ATL COM + 1.0|[Kreator składnika ATL COM + 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)|
|Odbiorca ATL OLEDB|[Kreator konsumenta ATL OLE DB](../atl/reference/atl-ole-db-consumer-wizard.md)|
|Dostawca ATL OLEDB|[Kreator dostawcy ATL OLE DB](../atl/reference/atl-ole-db-provider-wizard.md)|
|Strony właściwości ATL|[Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md)|
|Prosty obiekt ATL|[Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)|
|Dostawca zdarzeń WMI|Kreator dostawcy zdarzeń WMI|
|Dostawca wystąpień WMI|Kreator dostawcy interfejsu wystąpienia usługi WMI|

#### <a name="mfc"></a>MFC

|Szablon|Kreator|
|--------------|------------|
|Klasa MFC|[Kreator dodawania klasy MFC](../mfc/reference/mfc-add-class-wizard.md)|
|Klasa MFC z formantu ActiveX|[Dodawanie klasy z Kreatora kontrolek ActiveX](../ide/add-class-from-activex-control-wizard.md)|
|Klasa MFC z biblioteki typów|[Biblioteki typów, Kreator dodawania klasy z](../mfc/reference/add-class-from-typelib-wizard.md)|
|Odbiorca MFC ODBC|[Kreator użytkownika MFC ODBC](../mfc/reference/mfc-odbc-consumer-wizard.md)|

#### <a name="generic-classes"></a>Klasy ogólne

|Szablon|Kreator|
|--------------|------------|
|Rodzajowej klasy C++|[Kreatorze klasy generycznej C++](../ide/generic-cpp-class-wizard.md)|
