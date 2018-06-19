---
title: Formularz widoków (MFC) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- user interfaces [MFC], forms
- forms [MFC]
- applications [MFC], forms-based
- forms-based applications [MFC]
- forms [MFC], adding to applications
ms.assetid: efbe73c1-4ca4-4613-aac2-30d916e92c0e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87775c8afa1fa6eec8fbbdbbaa11bc9b5e6f1faa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349053"
---
# <a name="form-views-mfc"></a>Widoki formularzy (MFC)
Formularze można dodawać do dowolnej aplikacji Visual C++, która obsługuje biblioteki MFC, włączając [oparte na formularzach aplikacji](../mfc/reference/creating-a-forms-based-mfc-application.md) (jeden do którego widoku klasa pochodzi od `CFormView`). Jeśli aplikacja do obsługi formularzy nie został początkowo utworzony Visual C++ doda to obsługa po wstawieniu nowego formularza. SDI lub MDI aplikacji, które implementuje domyślny [architektura dokument/widok](../mfc/document-view-architecture.md), gdy użytkownik wybierze `New` polecenia (domyślnie na **pliku** menu), Visual C++ monituje użytkownika o Wybierz spośród dostępnych formularzy.  
  
 Za pomocą aplikacji SDI, gdy użytkownik wybierze `New` polecenia bieżącego wystąpienia formularza jest nadal uruchomiona, ale nowe wystąpienie aplikacji z wybranego formularza jest tworzony, jeśli nie można odnaleźć. W aplikacji MDI bieżącego wystąpienia formularza będzie kontynuował działanie, gdy użytkownik wybierze `New` polecenia.  
  
> [!NOTE]
>  Wstawieniem formularza do aplikacji opartych na oknach dialogowych (jednej klasy okien dialogowych, których opiera się na `CDialog` i jeden w widoku nie zaimplementowano klasy). Jednak bez architektury dokument/widok Visual C++ nie automatycznie implementuje **pliku**&#124;**nowy** funkcji. Należy utworzyć pozwala użytkownikowi na wyświetlanie dodatkowych formularzy, takie jak zaimplementowanie okno dialogowe z różnych strony właściwości.  
  
 Po włożeniu nowego formularza do aplikacji Visual C++ wykonuje następujące czynności:  
  
-   Tworzy klasę na podstawie jednej z klas styl formularza, które można wybrać (`CFormView`, `CRecordView`, `CDaoRecordView`, lub `CDialog`).  
  
-   Tworzy zasób okna dialogowego z odpowiednie style (lub użyć istniejącego zasobu okna dialogowego, które nie zostały skojarzone z klasą).  
  
     Jeśli wybierzesz istniejący zasób okna dialogowego, może być konieczne ustawić te style przy użyciu strony właściwości dla okna dialogowego. Style dla okna dialogowego musi zawierać:  
  
     **Ws_child —**= włączone  
  
     `WS_BORDER`= Wyłączone  
  
     **Ws_visible —**= wyłączone  
  
     **Ws_caption — =** wyłączone  
  
 Dla aplikacji, architektury dokument/widok **nowy formularz** polecenia (kliknij prawym przyciskiem myszy w widoku klasy) również:  
  
-   Tworzy **CDocument**— na podstawie klasy  
  
     Zamiast nową klasę utworzony, można użyć wszelkie istniejące **CDocument**— na podstawie klasy w projekcie.  
  
-   Generuje szablonu dokumentu (pochodną **CDocument**) przy użyciu zasobów ciągu, menu i ikony.  
  
     Można również utworzyć nową klasę, w której ma zostać utworzony szablon.  
  
-   Dodaje wywołanie **AddDocumentTemplate** w aplikacji `InitInstance` kodu.  
  
     Visual C++ dodaje ten kod dla każdego nowego formularza należy utworzyć, która dodaje formularza do listy dostępnych formularzy, gdy użytkownik wybierze `New` polecenia. Ten kod zawiera identyfikator zasobów i nazwy skojarzonego dokumentu, widoku i ramki klasy, które składają się nowy obiekt formularza.  
  
     Szablony dokumentów stanowią połączenie między dokumentów, okien ramowych i widoków. Dla pojedynczego dokumentu można utworzyć wiele szablonów.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Tworzenie aplikacji opartych na formularzach](../mfc/reference/creating-a-forms-based-mfc-application.md)  
  
-   [Wstawianie formularza do projektu](../mfc/inserting-a-form-into-a-project.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
