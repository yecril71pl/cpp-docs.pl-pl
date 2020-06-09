---
title: Tworzenie aplikacji kontenera dokumentów aktywnych
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], containers
- containers [MFC], active document
- active document containers [MFC], creating
- MFC COM, active document containment
- applications [MFC], active document container
ms.assetid: 14e2d022-a6c5-4249-8712-706b0f4433f7
ms.openlocfilehash: 860a8531a96a0671c808dba13523b492026eafe0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616351"
---
# <a name="creating-an-active-document-container-application"></a>Tworzenie aplikacji kontenera dokumentów aktywnych

Najprostszym i najbardziej zalecanym sposobem tworzenia aplikacji kontenera dokumentów aktywnych jest utworzenie aplikacji kontenera MFC EXE przy użyciu Kreatora aplikacji MFC, a następnie zmodyfikowanie aplikacji w celu obsługi zawierania dokumentów aktywnych.

#### <a name="to-create-an-active-document-container-application"></a>Aby utworzyć aplikację kontenera dokumentów aktywnych

1. W menu **plik** kliknij polecenie **projekt**w menu **Nowy** .

1. W lewym okienku kliknij pozycję **Visual C++** typ projektu.

1. Wybierz pozycję **aplikacja MFC** z okienka po prawej stronie.

1. Nazwij projekt *proj*, a następnie kliknij przycisk **OK**.

1. Wybierz stronę **obsługi dokumentu złożonego** .

1. Wybierz opcję **kontener** lub **kontener/pełny serwer** .

1. Zaznacz pole wyboru **kontener aktywnego dokumentu** .

1. Kliknij przycisk **Zakończ**.

1. Gdy Kreator aplikacji MFC zakończy generowanie aplikacji, Otwórz następujące pliki przy użyciu Eksplorator rozwiązań:

   - *MyProjview. cpp*

1. W *MyProjview. cpp*wprowadź następujące zmiany:

   - W programie `CMyProjView::OnPreparePrinting` Zamień zawartość funkcji na następujący kod:

     [!code-cpp[NVC_MFCDocView#56](codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting`zapewnia obsługę drukowania. Ten kod zastępuje `DoPreparePrinting` , który jest domyślnym przygotowaniem wydruku.

   Zawiera ona udoskonalony schemat drukowania w dokumencie aktywnym:

   - Możesz najpierw wywołać aktywny dokument za pomocą jego `IPrint` interfejsu i poinformować go, aby wydrukowałł się. To różni się od wcześniejszego zawierania OLE, w którym kontener musiał renderować obraz zawartego elementu na `CDC` obiekt drukarki.

   - Jeśli to się nie powiedzie, poinformuj zawarty element, aby wydrukował się za pomocą jego `IOleCommandTarget` interfejsu

   - Jeśli to się nie powiedzie, Utwórz własne renderowanie elementu.

   Statyczne funkcje członkowskie `COleDocObjectItem::OnPrint` i `COleDocObjectItem::OnPreparePrinting` , zgodnie z zaimplementowanym w poprzednim kodzie, obsługują ten udoskonalony schemat drukowania.

1. Dodaj dowolną implementację i skompiluj aplikację.

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](active-document-containment.md)
