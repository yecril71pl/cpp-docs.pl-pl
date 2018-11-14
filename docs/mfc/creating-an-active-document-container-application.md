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
ms.openlocfilehash: 5cdd3de8f4efcc23f89b81cb61302b5950938800
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520416"
---
# <a name="creating-an-active-document-container-application"></a>Tworzenie aplikacji kontenera dokumentów aktywnych

Najprostszy i najbardziej zalecany sposób tworzenia aplikacji kontenera dokumentów aktywnych jest, aby utworzyć aplikację kontenera MFC EXE za pomocą Kreatora aplikacji MFC, a następnie zmodyfikuj aplikację do obsługi zawieranie dokumentów aktywnych.

#### <a name="to-create-an-active-document-container-application"></a>Do tworzenia aplikacji kontenera dokumentów aktywnych

1. Z **pliku** menu, kliknij przycisk **projektu**z **New** podmenu.

1. W okienku po lewej stronie kliknij **Visual C++** typ projektu.

1. Wybierz **aplikacji MFC** w okienku po prawej stronie.

1. Nadaj projektowi nazwę *MyProj*, kliknij przycisk **OK**.

1. Wybierz **Obsługa dokumentów złożonych** strony.

1. Wybierz **kontenera** lub **kontener/pełny serwer** opcji.

1. Wybierz **kontener dokumentów aktywnych** pole wyboru.

1. Kliknij przycisk **Zakończ**.

1. Po zakończeniu pracy Kreatora aplikacji MFC, generowania aplikacji, należy otworzyć następujące pliki za pomocą Eksploratora rozwiązań:

   - *MyProjview.cpp*

1. W *MyProjview.cpp*, wprowadź następujące zmiany:

   - W `CMyProjView::OnPreparePrinting`, Zastąp zawartość funkcji następującym kodem:

     [!code-cpp[NVC_MFCDocView#56](../mfc/codesnippet/cpp/creating-an-active-document-container-application_1.cpp)]

   `OnPreparePrinting` zapewnia obsługę drukowania. Ten kod zastępuje `DoPreparePrinting`, który jest domyślne przygotowanie drukowania.

   Zawieranie dokumentów aktywnych zapewnia udoskonalony schemat drukowania:

   - Można wywołać aktywnego dokumentu za pośrednictwem jego `IPrint` interfejs i poinformuj go, aby wydrukował sam siebie. To różni się od poprzedniej zawierania OLE, kontener było renderować obraz zamkniętego elementu do drukarki `CDC` obiektu.

   - W przypadku niepowodzenia Przekaż zawartej element, aby wydrukował sam siebie za pośrednictwem jego `IOleCommandTarget` interfejsu

   - W przypadku niepowodzenia należy własne renderowania elementu.

   Statyczne funkcje Członkowskie `COleDocObjectItem::OnPrint` i `COleDocObjectItem::OnPreparePrinting`, zaimplementowanego w poprzednim kodzie obsługi tego udoskonalony schemat drukowania.

1. Dodaj własny implementacji i skompilować aplikację.

## <a name="see-also"></a>Zobacz też

[Zawieranie dokumentów aktywnych](../mfc/active-document-containment.md)

