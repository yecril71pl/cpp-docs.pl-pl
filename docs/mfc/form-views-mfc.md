---
title: Widoki formularzy (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
ms.openlocfilehash: 5e8912c9013175fe254b2f4a4a968a67fd071f39
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365299"
---
# <a name="form-views-mfc"></a>Widoki formularzy (MFC)

Formularze można dodawać do dowolnej aplikacji visual c++, która obsługuje biblioteki MFC, w `CFormView`tym [aplikacji opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md) (z której pochodzi klasa widoku ). Jeśli początkowo nie utworzysz aplikacji do obsługi formularzy, visual C++ doda tę obsługę po wstawieniu nowego formularza. W aplikacji SDI lub MDI, która implementuje domyślną [architekturę dokumentu/widoku,](../mfc/document-view-architecture.md)gdy użytkownik wybierze polecenie **Nowy** (domyślnie w menu **Plik),** program Visual C++ monituje użytkownika o wybranie spośród dostępnych formularzy.

W przypadku aplikacji SDI, gdy użytkownik wybierze **polecenie Nowy,** bieżące wystąpienie formularza będzie nadal działać, ale nowe wystąpienie aplikacji z wybranym formularzem jest tworzone, jeśli nie zostanie znalezione. W aplikacji MDI bieżące wystąpienie formularza jest nadal uruchamiane, gdy użytkownik wybierze polecenie **Nowy.**

> [!NOTE]
> Formularz można wstawić do aplikacji opartej na oknie dialogowym (takiej, której klasa okna dialogowego jest oparta, `CDialog` i takiej, w której nie jest implementowana żadna klasa widoku). Jednak bez architektury dokumentu/widoku visual C++ nie implementuje automatycznie **funkcji File**&#124;**New.** Należy utworzyć sposób wyświetlania dodatkowych formularzy przez użytkownika, na przykład implementując okno dialogowe z kartami z różnymi stronami właściwości.

Po wstawieniu nowego formularza do aplikacji program Visual C++ wykonuje następujące czynności:

- Tworzy klasę na podstawie jednej z klas w`CFormView`stylu `CRecordView` `CDaoRecordView`formularza, `CDialog`które wybierzesz ( , , , lub ).

- Tworzy zasób okna dialogowego z odpowiednimi stylami (lub można użyć istniejącego zasobu okna dialogowego, który nie został jeszcze skojarzony z klasą).

   Jeśli wybierzesz istniejący zasób okna dialogowego, może być konieczne ustawienie tych stylów przy użyciu strony Właściwości okna dialogowego. Style okna dialogowego muszą zawierać:

     **WS_CHILD**=Wł.

     **WS_BORDER**=Wył.

     **WS_VISIBLE**=Wył.

     **WS_CAPTION**=Wył.

W przypadku aplikacji opartych na architekturze dokumentu/widoku polecenie **Nowy formularz** (kliknięcie prawym przyciskiem myszy w widoku klasy) również:

- Tworzy `CDocument`klasę opartą na

   Zamiast tworzenia nowej klasy, można użyć dowolnej `CDocument`istniejącej klasy opartej na projekcie.

- Generuje szablon dokumentu (pochodny) `CDocument`z ciągiem, menu i zasobami ikon.

   Można również utworzyć nową klasę, na której można oprzeć szablon.

- Dodaje wywołanie `AddDocumentTemplate` w `InitInstance` kodzie aplikacji.

   Visual C++ dodaje ten kod dla każdego nowego formularza, który tworzysz, który dodaje formularz do listy dostępnych formularzy, gdy użytkownik wybierze **Nowe** polecenie. Ten kod zawiera identyfikator skojarzonego z formularzem zasobu oraz nazwy skojarzonych klas dokumentu, widoku i ramki, które razem tworzą nowy obiekt formularza.

   Szablony dokumentów służą jako połączenie między dokumentami, oknami ramek i widokami. W przypadku pojedynczego dokumentu można utworzyć wiele szablonów.

Aby uzyskać więcej informacji, zobacz:

- [Tworzenie aplikacji opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Wstawianie formularza do projektu](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
