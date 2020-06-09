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
ms.openlocfilehash: 94d8b7d026ee3aaf1bac9dee2226de6dd9382599
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615682"
---
# <a name="form-views-mfc"></a>Widoki formularzy (MFC)

Formularze można dodawać do dowolnych aplikacji Visual C++, które obsługują biblioteki MFC, w tym [aplikacji opartych na formularzach](reference/creating-a-forms-based-mfc-application.md) (z których pochodzi Klasa widoku `CFormView` ). Jeśli aplikacja nie została początkowo utworzona do obsługi formularzy, Visual C++ doda tę obsługę podczas wstawiania nowego formularza. W aplikacji SDI lub MDI implementującej domyślną [architekturę dokumentu/widoku](document-view-architecture.md), gdy użytkownik wybierze **nowe** polecenie (domyślnie w menu **plik** ), Visual C++ wyświetla użytkownika, aby wybrać spośród dostępnych formularzy.

Przy użyciu aplikacji SDI, gdy użytkownik wybierze **nowe** polecenie, bieżące wystąpienie formularza będzie nadal działać, ale tworzone jest nowe wystąpienie aplikacji z wybranym formularzem, jeśli nie zostanie ono odnalezione. W aplikacji MDI bieżące wystąpienie formularza jest nadal uruchamiane, gdy użytkownik wybierze **nowe** polecenie.

> [!NOTE]
> Formularz można wstawić do aplikacji opartej na oknach dialogowych (dla której jest oparta Klasa okna dialogowego `CDialog` i jeden, w którym nie zaimplementowano żadnej klasy widoku). Jednak bez architektury dokumentu/widoku Visual C++ nie implementuje automatycznie **pliku**&#124;**nową** funkcję. Należy utworzyć sposób wyświetlania dodatkowych formularzy przez użytkownika, na przykład przez implementację okna dialogowego z kartami z różnymi stronami właściwości.

Po wstawieniu nowego formularza do aplikacji Visual C++ wykonuje następujące czynności:

- Tworzy klasę na podstawie jednej z klas stylu formularza, które wybierasz ( `CFormView` , `CRecordView` , `CDaoRecordView` lub `CDialog` ).

- Tworzy zasób okna dialogowego z odpowiednimi stylami (lub można użyć istniejącego zasobu okna dialogowego, który nie został jeszcze skojarzony z klasą).

   W przypadku wybrania istniejącego zasobu okna dialogowego może być konieczne ustawienie tych stylów przy użyciu strony właściwości okna dialogowego. Style okna dialogowego muszą zawierać:

     **WS_CHILD**= włączone

     **WS_BORDER**= wyłączone

     **WS_VISIBLE**= wyłączone

     **WS_CAPTION**= wyłączone

W przypadku aplikacji opartych na architekturze dokumentu/widoku **nowy formularz** (kliknij prawym przyciskiem myszy w widok klasy) również:

- Tworzy `CDocument` klasę opartą na bazie

   Zamiast utworzyć nową klasę, można użyć dowolnej istniejącej `CDocument` klasy w projekcie.

- Generuje szablon dokumentu (pochodzący z `CDocument` ) za pomocą ciągu, menu i zasobów ikon.

   Możesz również utworzyć nową klasę, na której ma bazować szablon.

- Dodaje wywołanie do `AddDocumentTemplate` w `InitInstance` kodzie aplikacji.

   Visual C++ dodaje ten kod dla każdego utworzonego nowego formularza, który dodaje formularz do listy dostępnych formularzy, gdy użytkownik wybierze **nowe** polecenie. Ten kod zawiera skojarzony z formularzem identyfikator zasobu i nazwy skojarzonych klas dokumentów, widoków i ramek, które razem tworzą nowy obiekt formularza.

   Szablony dokumentów stanowią połączenie między dokumentami, oknami ramek i widokami. W przypadku jednego dokumentu można utworzyć wiele szablonów.

Aby uzyskać więcej informacji, zobacz:

- [Tworzenie aplikacji opartej na formularzach](reference/creating-a-forms-based-mfc-application.md)

- [Wstawianie formularza do projektu](inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)
