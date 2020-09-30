---
title: Dodawanie klasy
ms.date: 05/14/2019
f1_keywords:
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: b1c64505a63b8720ed7aee855f2bbbbdb9134e28
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505984"
---
# <a name="add-a-class"></a>Dodawanie klasy

Aby dodać klasę w projekcie Visual Studio C++, w **Eksplorator rozwiązań**kliknij projekt prawym przyciskiem myszy, wybierz polecenie **Dodaj**, a następnie wybierz pozycję **Klasa**. Spowoduje to otwarcie [okna dialogowego Dodaj klasę](#add-class-dialog-box).

Podczas dodawania klasy należy określić nazwę, która różni się od klas, które już istnieją w MFC lub ATL. Jeśli określisz nazwę, która już istnieje w jednej z bibliotek, środowisko IDE wyświetli komunikat o błędzie.

Jeśli Konwencja nazewnictwa projektu wymaga użycia istniejącej nazwy, można po prostu zmienić wielkość liter w nazwie, ponieważ w języku C++ jest rozróżniana wielkość liter. Na przykład, chociaż nie można nazwać klasy `CDocument` , można ją nazwać `cdocument` .

## <a name="in-this-section"></a>W tej sekcji

- [Jakiego rodzaju klasy chcesz dodać?](#what-kind-of-class-do-you-want-to-add)
- [Okno dialogowe Dodawanie klasy](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>Jakiego rodzaju klasy chcesz dodać?

W oknie dialogowym **Dodawanie klasy** po rozwinięciu węzła **Visual C++** w lewym okienku wyświetlane są kilka grup zainstalowanych szablonów. Grupy obejmują **środowiska CLR**, **ATL**, **MFC**i **C++**. Po wybraniu grupy w środkowym okienku zostanie wyświetlona lista dostępnych szablonów znajdujących się w tej grupie. Każdy szablon zawiera pliki i kod źródłowy, które są wymagane dla klasy.

Aby wygenerować nową klasę, wybierz szablon w środkowym okienku, wpisz nazwę klasy w polu **Nazwa** , a następnie wybierz pozycję **Dodaj**. Spowoduje to otwarcie **Kreatora dodawania klasy** , dzięki czemu można określić opcje dla klasy.

- Aby uzyskać więcej informacji o sposobach tworzenia klas MFC, zobacz [MFC Class](../mfc/reference/adding-an-mfc-class.md).

- Aby uzyskać więcej informacji o sposobach tworzenia klas ATL, zobacz [prosty obiekt ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
> Szablon **Dodaj obsługę ATL do MFC** nie tworzy klasy, ale zamiast tego konfiguruje projekt do korzystania z biblioteki ATL. Aby uzyskać więcej informacji, zobacz [Obsługa ATL w projekcie MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Aby utworzyć klasę języka C++, która nie korzysta z MFC, ATL lub CLR, użyj szablonu **klasy języka c++** w grupie zainstalowanych szablonów **języka c++** . Aby uzyskać więcej informacji, zobacz [Dodawanie klasy generycznej języka C++](../ide/adding-a-generic-cpp-class.md).

Dostępne są dwa rodzaje klas C++ opartych na formularzach. Pierwszy z nich, [Klasa CFormView](../mfc/reference/cformview-class.md), tworzy klasę MFC. Druga z nich tworzy klasę Windows Forms CLR.

## <a name="add-class-dialog-box"></a>Dodaj klasę — Okno dialogowe

Okno dialogowe **Dodawanie klasy** zawiera szablony, które umożliwiają:

- Otwórz Kreatora odpowiedniego kodu, jeśli jest dostępny. Aby uzyskać więcej informacji, zobacz [Dodawanie funkcji za pomocą kreatorów kodu](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- oraz

- Automatycznie Utwórz nową klasę przez dodanie odpowiednich plików i kodu źródłowego do projektu.

Możesz uzyskać dostęp do okna dialogowego **Dodaj klasę** z menu **projekt** , **Eksplorator rozwiązań**lub [Widok klasy](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Podczas próby dodania klasy, która nie jest odpowiednia dla bieżącego projektu, zostanie wyświetlony komunikat o błędzie. Wybierz **przycisk OK** , aby powrócić do okna dialogowego **Dodaj klasę** .

### <a name="add-class-templates"></a>Dodawanie szablonów klas

Istnieją cztery kategorie szablonów **dodawania klas** : .NET, ATL, MFC i Generic. Po wybraniu szablonu w okienku **Szablony** tekst opisujący wybór zostanie wyświetlony w okienku **Kategorie** i **Szablony** .

#### <a name="net"></a>.NET

|Szablon|Kreatora|
|--------------|------------|
|Usługa sieci Web ASP.NET|Niedostępne|
|Klasa składnika (.NET)|Niedostępne|
|Klasa Instalatora (.NET)|Niedostępne|
|Kontrolka użytkownika (.NET)|Niedostępne|
|Formularz systemu Windows (.NET)|Niedostępne|

#### <a name="atl"></a>ATL

|Szablon|Kreatora|
|--------------|------------|
|Dodawanie obsługi ATL do MFC|Niedostępne|
|Formant ATL|[Kreator kontrolki ATL](../atl/reference/atl-control-wizard.md)|
|Okno dialogowe ATL|[Kreator okna dialogowego ATL](../atl/reference/atl-dialog-wizard.md)|
|Prosty obiekt ATL|[Kreator prostych obiektów ATL](../atl/reference/atl-simple-object-wizard.md)|
|Dostawca zdarzeń WMI|Kreator dostawcy zdarzeń WMI|
|Dostawca wystąpień WMI|Kreator dostawcy wystąpień usługi WMI|

#### <a name="mfc"></a>MFC

|Szablon|Kreatora|
|--------------|------------|
|Klasa MFC|[Kreator dodawania klasy MFC](../mfc/reference/mfc-add-class-wizard.md)|

#### <a name="generic-classes"></a>Klasy ogólne

|Szablon|Kreatora|
|--------------|------------|
|Klasa generyczna C++|[Kreator klasy generycznej C++](./adding-a-generic-cpp-class.md#generic-c-class-wizard)|
