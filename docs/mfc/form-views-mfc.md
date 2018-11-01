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
ms.openlocfilehash: f092b9eca0fe0b4af40a5e1f6e77d3a0f1af74b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655627"
---
# <a name="form-views-mfc"></a>Widoki formularzy (MFC)

Formularzy można dodać do dowolnej aplikacji Visual C++, która obsługuje biblioteki MFC, łącznie z [aplikacji opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md) (jednej klasy widoku, którego jest tworzony na podstawie `CFormView`). Jeśli nie utworzono początkowo aplikacji do obsługi formularzy, Visual C++ doda tej obsługi dla Ciebie podczas wstawiania nowego formularza. W aplikacji SDI lub MDI, która implementuje domyślny [architektura dokument/widok](../mfc/document-view-architecture.md), gdy użytkownik wybierze **New** polecenia (domyślnie na **pliku** menu), Visual C++ monituje użytkownika do wyboru dostępne formularze.

Za pomocą aplikacji interfejsu SDI, gdy użytkownik wybierze **New** polecenia bieżące wystąpienie formularza będzie nadal działać, ale nowe wystąpienie aplikacji z wybranego formularza jest tworzony, jeśli nie został znaleziony. W aplikacji MDI, bieżące wystąpienie formularza będzie nadal działać, gdy użytkownik wybierze **New** polecenia.

> [!NOTE]
>  Formularz można wstawić do oparta na oknach dialogowych aplikacji (których klasy okien dialogowych opiera się na jednym `CDialog` i jeden w widoku nie zaimplementowano klasy). Jednak bez architektury dokument/widok Visual C++ nie automatycznie implementuje **pliku**&#124;**New** funkcji. Należy utworzyć zapewniającej użytkownikowi na wyświetlanie dodatkowych formularzy, takich jak zaimplementowanie okno dialogowe na różnych stronach właściwości.

Po wstawieniu nowy formularz w swojej aplikacji Visual C++ zapewnia następujące funkcje:

- Tworzy klasę na podstawie jednej z klas styl formularza, które możesz wybrać (`CFormView`, `CRecordView`, `CDaoRecordView`, lub `CDialog`).

- Tworzy zasobu okna dialogowego z odpowiednie style (lub użyć istniejącego zasobu okna dialogowego, który nie został jeszcze skojarzone z klasą).

   Jeśli wybierzesz istniejącego zasobu okna dialogowego, może być konieczne należy ustawić te style, używając strony właściwości dla okna dialogowego. Style dla okna dialogowego należy uwzględnić:

     **WS_CHILD**= włączone

     **WS_BORDER**= wyłączone

     **WS_VISIBLE**= wyłączone

     **WS_CAPTION =** wyłączone

W przypadku aplikacji, w zależności od architektury dokument/widok **nowy formularz** polecenia (kliknij prawym przyciskiem myszy w widoku klas) również:

- Tworzy `CDocument`— na podstawie klasy

   Zamiast nowej klasy, utworzony, można użyć wszystkich istniejących `CDocument`— na podstawie klasy w projekcie.

- Generuje szablonu dokumentu (pochodną `CDocument`) przy użyciu zasobów ciągu, menu i ikony.

   Można również utworzyć nową klasę, na którym ma zostać utworzony szablon.

- Dodaje wywołanie `AddDocumentTemplate` w Twojej aplikacji `InitInstance` kodu.

   Visual C++ dodaje ten kod dla każdego nowego formularza należy utworzyć, który dodaje formularza do listy dostępnych formularzy, gdy użytkownik wybierze **New** polecenia. Ten kod zawiera identyfikator skojarzonego zasobu formularza i nazwy powiązany dokument, widoku i ramki klas, które razem tworzą nowy obiekt formularza.

   Szablony dokumentów służą jako połączenie między dokumentami, oknami ramek i widokami. Dla pojedynczego dokumentu można utworzyć wiele szablonów.

Aby uzyskać więcej informacji, zobacz:

- [Tworzenie aplikacji opartej na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Wstawianie formularza do projektu](../mfc/inserting-a-form-into-a-project.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
