---
title: Tworzenie interfejsu COM
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.com.creating.interfaces
- vc.codewiz.com.editing.interfaces
helpviewer_keywords:
- COM interfaces, creating
- methods [C++], adding to COM interfaces
- COM interfaces, editing
- properties [C++], adding to COM interfaces
ms.assetid: 1be84d3c-6886-4d1e-8493-56c4d38a96d4
ms.openlocfilehash: dfc4b09f4fa42b179bdef91877e0a004caa69187
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345230"
---
# <a name="create-a-com-interface"></a>Tworzenie interfejsu COM

Visual C++ zapewnia kreatory i szablony do tworzenia projektów używających definiowanie interfejsów COM i dispinterfaces dla obiektów COM i klasy automatyzacji.

Te kreatory umożliwia wykonywanie następujących trzech typowych zadań:

- [Dodaj obsługę ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

  Dodaj obsługę ATL do aplikacji MFC, po utworzeniu projektu MFC przy użyciu [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md) , a następnie uruchamiając **Dodawanie obsługi ATL do MFC** kreatora kodów. Ta funkcja dotyczy tylko proste obiekty COM, dodane do projektu biblioteki DLL lub pliku wykonywalnego MFC. Te obiekty ATL może mieć więcej niż jednego interfejsu.

- [Tworzenie kontrolki MFC ActiveX](../mfc/reference/creating-an-mfc-activex-control.md).

  Otwórz [kreatora kontrolek MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md) tworzenia kontrolki ActiveX z dispinterface i mapę zdarzeń zdefiniowanych w pliku .idl i klasy kontrolek, odpowiednio.

- [Dodawanie kontrolki ATL](../atl/reference/adding-an-atl-control.md).

  Użyj kombinacji [Kreator projektów ATL](../atl/reference/atl-project-wizard.md) i [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md) do tworzenia formantu ATL ActiveX.

  Można również dodać kontrolki ATL do projektu MFC, do którego została dodana obsługa biblioteki ATL, zgodnie z powyższym opisem. Ponadto jeśli zostanie wybrana **kontrolka ATL** w **Dodaj klasę** okno dialogowe, a jeszcze nie dodano obsługę ATL do projektu MFC, Visual Studio wyświetli okno dialogowe z potwierdzeniem, dodając obsługę ATL do usługi Projekt MFC.

  Ten kreator generuje źródło IDL i mapy COM w klasach projektu.

Po projekcie ATL otworzyć, [Dodaj klasę](../ide/add-class-dialog-box.md) okno dialogowe umożliwia wybór dodatkowe kreatorów i szablonów, aby dodać interfejsy modelu COM do projektu. Zezwalaj na następujących kreatorów, ustanowienia co najmniej jeden interfejs dla obiektu:

- [Kreator składnika ATL COM + 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)
- [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)
- [Kreator składników stron active server ATL](../atl/reference/atl-active-server-page-component-wizard.md)
- [Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)

Ponadto można zaimplementować nowe interfejsy COM formantu. Po prostu kliknij prawym przyciskiem myszy obiekt klasy formantu w widoku klas i wybierz [implementuj interfejs](../ide/implement-interface-wizard.md).

> [!NOTE]
> Program Visual Studio nie udostępnia kreatora, aby dodać interfejs do projektu. Można dodać interfejs do projektu ATL lub do [Dodaj Obsługa biblioteki ATL do projektu MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) przez dodanie przy użyciu prostego obiektu [Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md). Alternatywnie Otwórz pliku .idl projektu i Utwórz interfejs, wpisując:

```
interface IMyInterface {
};
```

Aby uzyskać więcej informacji, zobacz [zaimplementować interfejs](../ide/implementing-an-interface-visual-cpp.md) i [dodawać obiekty i kontrolki do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md).

Visual C++ oferuje kilka sposobów, aby wyświetlić i [Edytuj interfejsów COM](#edit-a-com-interface) zdefiniowane dla Twoich projektów. [Widok klas](/visualstudio/ide/viewing-the-structure-of-code) Wyświetla ikony dla dowolnej interfejsu dispinterface zdefiniowane w pliku .idl w projekcie języka C++.

Dla klas obiektów oparty na bibliotece ATL COM widoku klasy odczytuje mapy COM w klasy ATL do wyświetlania relacji między klasą ATL i wszystkie interfejsy, które implementuje.

W widoku klas i jego menu skrótów można pracować z interfejsów w następujący sposób:

- Dodaj obiekty ATL z aplikacją oparty na bibliotece MFC.
- Dodaj metody, właściwości i zdarzenia.
- Przechodzić bezpośrednio do elementu kod interfejsu, klikając ten element.

## <a name="in-this-section"></a>W tej sekcji

- [Edytowanie interfejsu COM](#edit-a-com-interface)

## <a name="edit-a-com-interface"></a>Edytowanie interfejsu COM

Za pomocą poleceń menu skrótów w widoku klas, można zdefiniować nowej metody i właściwości dla interfejsów COM w projektach języka Visual C++. Z przybornika można również definiować zdarzenia dla formantów ActiveX.

ATL i MFC oparte na modelu COM klas obiektów można edytować implementację klasy, w tym samym czasie edytowania interfejsu.

> [!NOTE]
> Dla interfejsów, które zostały zdefiniowane poza **Dodaj klasę** okno dialogowe, Visual C++ dodaje metody lub właściwości do pliku .idl i dodanie klasy zastępcze dla klas, które implementują metody, nawet wtedy, gdy interfejsy są dodawane ręcznie.

Następujących kreatorów trzy pomóc dostosować istniejące interfejsy. Są one dostępne z widoku klasy:

|Kreator|Typ projektu|
|------------|------------------|
|[Kreator dodawania właściwości](../ide/names-add-property-wizard.md)|Projekty ATL lub MFC, obsługa ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać właściwość.<br /><br />Visual C++ wykrywa typ projektu i modyfikuje opcje w Kreatorze dodawania właściwości, zgodnie z potrzebami:<br /><br />– W przypadku dispinterfaces w projekty utworzone za pomocą [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), wywoływanie Kreator dodawania właściwości udostępnia opcje, które określone z MFC.<br />– W przypadku interfejsów kontrolki MFC ActiveX Kreator dodawania właściwości zawiera listę podstawowych metod i właściwości, które mogą używać zgodnie z postanowieniami lub dostosowywanie kontrolki.<br />— Dla wszystkich innych interfejsów kreatory Dodaj właściwość zapewniają przydatne w większości sytuacji opcje.|
|[Kreator dodawania metody](../ide/add-method-wizard.md)|Projekty ATL lub MFC, obsługa ATL. Kliknij prawym przyciskiem myszy interfejs, do którego chcesz dodać metody.<br /><br />Visual C++ wykrywa typ projektu i modyfikuje opcje w Kreatorze metody dodawania, zgodnie z potrzebami:<br /><br />– W przypadku dispinterfaces w projekty utworzone za pomocą [Kreator aplikacji MFC](../mfc/reference/mfc-application-wizard.md), za pomocą Kreatora dodawania metody udostępnia opcje, które określone z MFC.<br />– W przypadku interfejsów kontrolki MFC ActiveX Kreator dodawania metody zawiera listę podstawowych metod i właściwości, które mogą używać zgodnie z postanowieniami lub dostosowywanie kontrolki.<br />— Dla wszystkich innych interfejsów **Dodaj metodę** kreatorów udostępniają opcje przydatne w większości sytuacji.|

Ponadto można zaimplementować nowe interfejsy COM formantu. Po prostu kliknij prawym przyciskiem myszy obiekt klasy formantu w widoku klas i wybierz [implementuj interfejs](../ide/implement-interface-wizard.md).
