---
title: Dodaj klasę
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: fa53c2af5cd3e81c2d4877ef255430eac9525aad
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708139"
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
|Kontrolka ATL|[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)|
|Okno dialogowe ATL|[Kreator okna dialogowego ATL](../atl/reference/atl-dialog-wizard.md)|
|Prosty obiekt ATL|[Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)|
|Dostawca zdarzeń WMI|Kreator dostawcy zdarzeń WMI|
|Dostawca wystąpień WMI|Kreator dostawcy interfejsu wystąpienia usługi WMI|

#### <a name="mfc"></a>MFC

|Szablon|Kreator|
|--------------|------------|
|Klasa MFC|[Kreator dodawania klasy MFC](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>Klasy ogólne

|Szablon|Kreator|
|--------------|------------|
|Rodzajowej klasy C++|[Kreatorze klasy generycznej C++](../ide/generic-cpp-class-wizard.md)|
