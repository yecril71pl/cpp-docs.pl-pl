---
title: Okno dialogowe Dodaj klasę
ms.date: 11/04/2016
f1_keywords:
- vc.addclass
helpviewer_keywords:
- Add Class dialog box
ms.assetid: 916259b8-8e5f-4267-bd10-313483beba67
ms.openlocfilehash: 405f88f7f77ea75584ec3cfd76af1ea9a0457ed6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643199"
---
# <a name="add-class-dialog-box"></a>Okno dialogowe Dodaj klasę

**Dodaj klasę** okno dialogowe zawiera szablony, które pozwalają na:

- Otwórz odpowiedniego kreatora kodów, jeśli jest dostępny. Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji z kreatorami kodów](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- lub —

- Automatycznie Utwórz nowej klasy, dodając odpowiednie pliki i kod źródłowy do projektu.

Możesz uzyskać dostęp **Dodaj klasę** okno dialogowe z **projektu** menu **Eksploratora rozwiązań**, lub [Widok klas](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
>  Gdy spróbujesz dodać klasę, która nie jest przeznaczone do bieżącego projektu, otrzymasz komunikat o błędzie. Kliknij przycisk **OK** aby powrócić do **Dodaj klasę** okno dialogowe.

## <a name="add-class-templates"></a>Dodawanie szablonów klas

Istnieją cztery kategorie **Dodaj klasę** szablonów: .NET, ATL, MFC i ogólnych. Po wybraniu szablonu w **szablony** okienku tekst opisujący wybór pojawi się w obszarze **kategorie** i **szablony** okienka.

### <a name="net"></a>.NET

|Szablon|Kreator|
|--------------|------------|
|Usługa sieci Web ASP.NET|Niedostępne|
|Klasa składników (.NET)|Niedostępne|
|Klasa Instalatora (.NET)|Niedostępne|
|Kontrolka użytkownika (.NET)|Niedostępne|
|Formularz Windows (.NET)|Niedostępne|

### <a name="atl"></a>ATL

|Szablon|Kreator|
|--------------|------------|
|Dodaj obsługę ATL do MFC|Niedostępne|
|Składnika strony Active Server ATL|[Kreator składników stron Active Server Page ATL](../atl/reference/atl-active-server-page-component-wizard.md)|
|Kontrolka ATL|[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)|
|Okno dialogowe ATL|[Kreator okna dialogowego ATL](../atl/reference/atl-dialog-wizard.md)|
|Składnik ATL COM + 1.0|[Kreator składników ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)|
|Odbiorca ATL OLEDB|[Kreator konsumenta OLE DB ATL](../atl/reference/atl-ole-db-consumer-wizard.md)|
|Dostawca ATL OLEDB|[Kreator dostawcy interfejsu OLE DB ATL](../atl/reference/atl-ole-db-provider-wizard.md)|
|Strony właściwości ATL|[Kreator strony właściwości ATL](../atl/reference/atl-property-page-wizard.md)|
|Prosty obiekt ATL|[Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)|
|Dostawca zdarzeń WMI|Kreator dostawcy zdarzeń WMI|
|Dostawca wystąpień WMI|Kreator dostawcy interfejsu wystąpienia usługi WMI|

### <a name="mfc"></a>MFC

|Szablon|Kreator|
|--------------|------------|
|Klasa MFC|[Kreator dodawania klasy MFC](../mfc/reference/mfc-add-class-wizard.md)|
|Klasa MFC z formantu ActiveX|[Kreator dodawania klasy z kontrolki ActiveX](../ide/add-class-from-activex-control-wizard.md)|
|Klasa MFC z biblioteki typów|[Biblioteki typów, Kreator dodawania klasy z](../mfc/reference/add-class-from-typelib-wizard.md)|
|Odbiorca MFC ODBC|[Kreator użytkownika MFC ODBC](../mfc/reference/mfc-odbc-consumer-wizard.md)|

### <a name="generic-classes"></a>Klasy ogólne

|Szablon|Kreator|
|--------------|------------|
|Rodzajowej klasy C++|[Kreator rodzajowej klasy C++](../ide/generic-cpp-class-wizard.md)|

## <a name="see-also"></a>Zobacz też

[Dodawanie funkcji członkowskiej](../ide/adding-a-member-function-visual-cpp.md)<br>
[Dodawanie zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Zastępowanie funkcji wirtualnych](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Handler komunikatów MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Nawigacja w strukturze klas](../ide/navigating-the-class-structure-visual-cpp.md)