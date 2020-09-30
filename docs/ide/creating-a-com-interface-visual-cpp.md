---
title: Tworzenie interfejsu COM
ms.date: 05/14/2019
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: 6ad8d50049d34a711937f3d1f73157ce26f69808
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509694"
---
# <a name="create-a-com-interface"></a>Tworzenie interfejsu COM

Program Visual Studio udostępnia kreatorom i szablonom tworzenie projektów, które używają modelu COM definiującego interfejsy i dispinterfaces dla obiektów COM i klas automatyzacji.

Za pomocą tych kreatorów można wykonać następujące trzy typowe zadania:

- [Dodaj obsługę ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

  Dodawanie obsługi ATL do aplikacji MFC po utworzeniu projektu MFC przy użyciu [Kreatora aplikacji MFC](../mfc/reference/mfc-application-wizard.md) , a następnie uruchomieniu kreatora **dodawania obsługi biblioteki ATL do kodu MFC** . Ta obsługa dotyczy tylko prostych obiektów COM dodanych do pliku wykonywalnego MFC lub projektu DLL. Te obiekty ATL mogą mieć więcej niż jeden interfejs.

- [Utwórz kontrolkę ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md).

  Otwórz [Kreatora kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md) , aby utworzyć kontrolkę ActiveX z dispinterface i mapę zdarzeń zdefiniowaną odpowiednio w pliku. idl i klasy Control.

- [Dodaj kontrolkę ATL](../atl/reference/adding-an-atl-control.md).

  Użyj kombinacji [Kreatora projektu ATL](../atl/reference/atl-project-wizard.md) i [Kreatora kontrolki ATL](../atl/reference/atl-control-wizard.md) , aby utworzyć formant ActiveX ATL.

  Można również dodać formant ATL do projektu MFC, do którego dodano obsługę ATL, zgodnie z powyższym opisem. Ponadto, jeśli wybierzesz opcję **formant ATL** w oknie dialogowym **Dodaj klasę** i nie Dodaliśmy jeszcze obsługi ATL do projektu MFC, program Visual Studio wyświetli okno dialogowe, które potwierdzi Dodawanie obsługi ATL do projektu MFC.

  Ten Kreator generuje Źródło IDL i mapę COM w klasach projektu.

Po otwarciu projektu ATL, okno dialogowe [Dodawanie klasy](./adding-a-class-visual-cpp.md#add-class-dialog-box) umożliwia wybranie dodatkowych kreatorów i szablonów w celu dodania interfejsów com do projektu. Poniższe kreatory umożliwiają ustanowienie jednego lub kilku interfejsów dla obiektu:

- [Kreator składnika ATL COM+ 1,0](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)
- [Kreator składnika strony aktywnego serwera ATL](../atl/reference/atl-active-server-page-component-wizard.md)
- [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)

Ponadto można zaimplementować nowe interfejsy w formancie COM. Po prostu kliknij prawym przyciskiem myszy klasę formantu obiektu w Widok klasy i wybierz polecenie [Implementuj interfejs](./implementing-an-interface-visual-cpp.md#implement-interface-wizard).

> [!NOTE]
> Program Visual Studio nie udostępnia kreatora umożliwiającego dodanie interfejsu do projektu. Można dodać interfejs do projektu ATL lub [dodać obsługę ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodanie prostego obiektu za pomocą [Kreatora prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz plik. idl projektu i Utwórz interfejs, wpisując:

```
interface IMyInterface {
};
```

Aby uzyskać więcej informacji, zobacz [implementowanie interfejsu](../ide/implementing-an-interface-visual-cpp.md) i [Dodawanie obiektów i kontrolek do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ oferuje kilka sposobów wyświetlania i [edytowania interfejsów com](#edit-a-com-interface) zdefiniowanych dla projektów. [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code) wyświetla ikony dowolnego interfejsu lub dispinterface zdefiniowane w pliku. idl w projekcie języka C++.

W przypadku klas obiektów COM opartych na ATL Widok klasy odczytuje mapę COM w klasie ATL, aby wyświetlić relacje między klasą ATL i wszystkimi interfejsami, które implementuje.

W Widok klasy i jego menu skrótów można korzystać z interfejsów w następujący sposób:

- Dodaj obiekty ATL do aplikacji opartej na MFC.
- Dodawanie metod, właściwości i zdarzeń.
- Przejdź bezpośrednio do kodu interfejsu elementu przez dwukrotne kliknięcie elementu.

## <a name="in-this-section"></a>W tej sekcji

- [Edytowanie interfejsu COM](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>Edytowanie interfejsu COM

Korzystając z poleceń z menu skrótów Widok klasy, można definiować nowe metody i właściwości interfejsów COM w projektach programu Visual Studio C++. Z przybornika można także definiować zdarzenia dla formantów ActiveX.

W przypadku klas obiektów COM opartych na ATL i MFC można edytować implementację klasy w tym samym czasie, edytując interfejs.

> [!NOTE]
> W przypadku interfejsów, które zostały zdefiniowane poza oknem dialogowym **Dodaj klasę** , Visual C++ dodaje metody lub właściwości do pliku. idl i dodaje do klas, które implementują metody, nawet gdy interfejsy są dodawane ręcznie.

Poniższe trzy kreatory ułatwiają Dostosowywanie istniejących interfejsów. Są one dostępne w Widok klasy:

|Kreatora|Project type (Typ projektu)|
|------------|------------------|
|[Kreator dodawania właściwości](./adding-a-property-visual-cpp.md#names-add-property-wizard)|Projekty ATL lub MFC obsługujące ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać właściwość.<br /><br />Visual C++ wykrywa typ projektu i modyfikuje opcje w Kreatorze dodawania właściwości w razie potrzeby:<br /><br />— Dla dispinterfaces w projektach utworzonych przy użyciu [Kreatora aplikacji MFC](../mfc/reference/mfc-application-wizard.md)wywoływanie Kreatora dodawania właściwości zapewnia opcje specyficzne dla MFC.<br />-Dla interfejsów kontrolek ActiveX MFC, Kreator dodawania właściwości zawiera listę metod i właściwości, które można wykorzystać jako dostarczone lub dostosowane do kontrolki.<br />— Dla wszystkich innych interfejsów kreatorzy dodawania właściwości oferują opcje przydatne w większości sytuacji.|
|[Kreator dodawania metody](./adding-a-method-visual-cpp.md#add-method-wizard)|Projekty ATL lub MFC obsługujące ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać metodę.<br /><br />Visual C++ wykrywa typ projektu i modyfikuje opcje w Kreatorze dodawania metody w razie potrzeby:<br /><br />— Dla dispinterfaces w projektach utworzonych za pomocą [Kreatora aplikacji MFC](../mfc/reference/mfc-application-wizard.md)przy użyciu Kreatora dodawania metody dostępne są opcje specyficzne dla MFC.<br />-Dla interfejsów kontrolek ActiveX MFC, Kreator dodawania metody udostępnia listę metod i właściwości, które można wykorzystać jako dostarczone lub dostosowane do kontrolki.<br />— W przypadku wszystkich innych interfejsów kreatorzy **dodawania metody** zapewniają opcje przydatne w większości sytuacji.|

Ponadto można zaimplementować nowe interfejsy w formancie COM. Po prostu kliknij prawym przyciskiem myszy klasę formantu obiektu w Widok klasy i wybierz polecenie [Implementuj interfejs](./implementing-an-interface-visual-cpp.md#implement-interface-wizard).
