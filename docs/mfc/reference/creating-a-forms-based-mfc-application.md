---
title: Tworzenie aplikacji MFC opartej na formularzach
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcforms.project
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
ms.openlocfilehash: d95a5ddd5b8504bedc8136ae553b62b3ee6740f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518602"
---
# <a name="creating-a-forms-based-mfc-application"></a>Tworzenie aplikacji MFC opartej na formularzach

Formularz to okno dialogowe z kontrolkami, które umożliwiają użytkownikowi dostęp i ewentualnie modyfikowanie danych. Można utworzyć aplikację, w której użytkownik wybiera jeden z wielu formularzy. Często, aplikacją opartą na formularzach umożliwia formularzy dostępu użytkownika poprzez kliknięcie **New** z **pliku** menu. Aplikacja oparta na oknach dialogowych, która nie zapewnia użytkownikom dostęp do **New** opcji **pliku** menu jest również uważana za aplikacją opartą na formularzach.

Aplikacja oparta na formularzach wykorzystująca mechanizm interfejsu pojedynczego dokumentu (SDI) umożliwia działanie równocześnie tylko jednego wystąpienie danego formularza. Można uruchomić różne formularze w tym samym czasie z aplikacji interfejsu SDI opartego na formularzach, wybierając nowy formularz z **New** opcji **pliku** menu.

W przypadku utworzenia aplikacji opartej na formularzach wykorzystującej mechanizm interfejsu wielu dokumentów (MDI) będzie ona obsługiwała wiele wystąpień tego samego formularza.

W aplikacji z obsługą wielu dokumentów najwyższego poziomu niejawnym obiektem nadrzędnym dla dokumentu jest pulpit, a ramka dokumentu nie ogranicza się do obszaru klienckiego aplikacji. Można otworzyć wiele wystąpień dokumentu, każdy z własną ramką, menu i ikoną paska zadań. Kolejne wystąpienia dokumentów można zamknąć pojedynczo, ale w przypadku wybrania **zakończenia** opcję **pliku** menu pierwszego wystąpienia aplikacji spowoduje zamknięcie wszystkich wystąpień.

Aplikacje obsługujące interfejsy SDI i MDI oraz wiele dokumentów najwyższego poziomu są oparte na formularzach i wykorzystują architekturę dokument/widok.

Każda aplikacja oparta na oknach dialogowych jest z definicji oparta na formularzach. Aplikacja oparta na oknach dialogowych nie używa architektury dokument/widok, w związku z czym trzeba zarządzać tworzeniem własnych dodatkowych formularzy i metodami dostępu do nich.

Klasa bazowa dla aplikacji opartych na formularzach jest [CFormView](../../mfc/reference/cformview-class.md). Jeśli aplikacja obsługuje bazę danych, można również wybrać dowolną klasę pochodzącą od klasy `CFormView`. Formularzem jest dowolne okno pochodzące od klasy `CFormView` albo od dowolnej klasy dziedziczącej z klasy `CFormView`.

Nawet wtedy, gdy takie jak używana klasa bazowa [CView](../../mfc/reference/cview-class.md), można później przekształcić swoje aplikacje oparte na formularzach przez [Dodawanie klasy MFC](../../mfc/reference/adding-an-mfc-class.md) pochodną `CFormView` i sprawdzanie **tym Generowanie zasoby** pola wyboru w [Kreator klas MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).

Po ukończeniu pracy w kreatorze zostanie otwarty projekt. Jeśli jako klasę bazową wybrano `CFormView` (lub klasę dziedziczącą z klasy `CFormView`) lub jeśli utworzono aplikację opartą na oknach dialogowych, zostanie otwarty edytor okien dialogowych. Teraz można przystąpić do projektowania pierwszego formularza.

### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Aby rozpocząć tworzenie pliku wykonywalnego MFC opartego na formularzach

1. Postępuj zgodnie z instrukcjami [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).

1. W Kreatorze aplikacji MFC [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) wybierz opcję **Obsługa architektury dokument/widok** pole wyboru.

1. Wybierz **pojedynczego dokumentu**, **wiele dokumentów**, lub **wiele dokumentów najwyższego poziomu**.

    > [!NOTE]
    >  W przypadku wybrania SDI, MDI lub obsługi aplikacji interfejsu wielu dokumentów najwyższego poziomu, domyślnie `CView` jest ustawiony jako klasę bazową widoku aplikacji w [wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony kreatora. Aby utworzyć aplikację opartą na formularzach, jako klasę bazową widoku aplikacji należy wybrać klasę `CFormView`. Kreator nie zapewnia funkcji drukowania dla aplikacji opartej na formularzach.

1. Na pozostałych stronach kreatora skonfiguruj inne opcje projektu.

1. Kliknij przycisk **Zakończ** do zostanie wygenerowany szkielet aplikacji.

Aby uzyskać więcej informacji, zobacz:

- [Pochodne klasy widoków](../../mfc/derived-view-classes-available-in-mfc.md)

- [Alternatywy dla architektury dokument/widok](../../mfc/alternatives-to-the-document-view-architecture.md)

- [Opcje do wyboru przy projektowaniu aplikacji](../../mfc/application-design-choices.md)

## <a name="see-also"></a>Zobacz też

[Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)<br/>
[Widoki formularzy](../../mfc/form-views-mfc.md)<br/>
[Tworzenie aplikacji MFC w stylu eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)<br/>
[Tworzenie aplikacji MFC w stylu przeglądarki internetowej](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

