---
title: Tworzenie aplikacji MFC opartej na formularzach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfcforms.project
dev_langs: C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 764721114bb87127c892563211f7fcc85171ea68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-forms-based-mfc-application"></a>Tworzenie aplikacji MFC opartej na formularzach
Formularz to okno dialogowe z kontrolkami, które umożliwiają użytkownikowi dostęp i ewentualnie modyfikowanie danych. Można utworzyć aplikację, w której użytkownik wybiera jeden z wielu formularzy. Zazwyczaj oparte na formularzach aplikacji umożliwia formularzy dostępu użytkownika przez kliknięcie **nowy** z **pliku** menu. Aplikacji opartych na oknach dialogowych, który nie zapewnia użytkownikom dostęp do **nowy** opcji **pliku** menu jest traktowana jako aplikację na podstawie formularzy.  
  
 Aplikacja oparta na formularzach wykorzystująca mechanizm interfejsu pojedynczego dokumentu (SDI) umożliwia działanie równocześnie tylko jednego wystąpienie danego formularza. Istnieje możliwość uruchamiania różnych formularzach jednocześnie z SDI oparte na formularzach aplikacji przez wybranie nowego formularza z **nowy** opcji **pliku** menu.  
  
 W przypadku utworzenia aplikacji opartej na formularzach wykorzystującej mechanizm interfejsu wielu dokumentów (MDI) będzie ona obsługiwała wiele wystąpień tego samego formularza.  
  
 W aplikacji z obsługą wielu dokumentów najwyższego poziomu niejawnym obiektem nadrzędnym dla dokumentu jest pulpit, a ramka dokumentu nie ogranicza się do obszaru klienckiego aplikacji. Można otworzyć wiele wystąpień dokumentu, każdy z własną ramką, menu i ikoną paska zadań. Zamknij kolejne wystąpienia dokumenty pojedynczo, ale po zaznaczeniu `Exit` opcję **pliku** menu początkowej wystąpienia aplikacji, zamyka wszystkie wystąpienia.  
  
 Aplikacje obsługujące interfejsy SDI i MDI oraz wiele dokumentów najwyższego poziomu są oparte na formularzach i wykorzystują architekturę dokument/widok.  
  
 Każda aplikacja oparta na oknach dialogowych jest z definicji oparta na formularzach. Aplikacja oparta na oknach dialogowych nie używa architektury dokument/widok, w związku z czym trzeba zarządzać tworzeniem własnych dodatkowych formularzy i metodami dostępu do nich.  
  
 Klasa podstawowa dla aplikacji opartej na formularzu jest [CFormView](../../mfc/reference/cformview-class.md). Jeśli aplikacja obsługuje bazę danych, można również wybrać dowolną klasę pochodzącą od klasy `CFormView`. Formularzem jest dowolne okno pochodzące od klasy `CFormView` albo od dowolnej klasy dziedziczącej z klasy `CFormView`.  
  
 Nawet w przypadku takich jak używać klasy podstawowej [CView](../../mfc/reference/cview-class.md), później pozwala aplikacji na podstawie formularzy przez [Dodawanie klasy MFC](../../mfc/reference/adding-an-mfc-class.md) pochodną `CFormView` i sprawdzanie **Generowanie opcję zasoby** checkbox w [Kreator klas MFC](../../mfc/reference/document-template-strings-mfc-add-class-wizard.md).  
  
 Po ukończeniu pracy w kreatorze zostanie otwarty projekt. Jeśli jako klasę podstawową wybrano `CFormView` (lub klasę dziedziczącą z klasy `CFormView`) lub jeśli utworzono aplikację opartą na oknach dialogowych, zostanie otwarty edytor okien dialogowych. Teraz można przystąpić do projektowania pierwszego formularza.  
  
### <a name="to-begin-creating-a-forms-based-mfc-executable"></a>Aby rozpocząć tworzenie pliku wykonywalnego MFC opartego na formularzach  
  
1.  Postępuj zgodnie z instrukcjami w [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  W Kreatorze aplikacji MFC [typu aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) wybierz pozycję **wsparcie dla architektury dokument/widok** pole wyboru.  
  
3.  Wybierz **pojedynczego dokumentu**, **wielu dokumentów**, lub **wiele dokumentów najwyższego poziomu**.  
  
    > [!NOTE]
    >  W przypadku wybrania SDI MDI i aplikacji interfejsu wielu dokumentów najwyższego poziomu, domyślnie `CView` jest ustawiony jako klasę podstawową dla widoku aplikacji w [wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) stronie kreatora. Aby utworzyć aplikację opartą na formularzach, jako klasę podstawową widoku aplikacji należy wybrać klasę `CFormView`. Kreator nie zapewnia funkcji drukowania dla aplikacji opartej na formularzach.  
  
4.  Na pozostałych stronach kreatora skonfiguruj inne opcje projektu.  
  
5.  Kliknij przycisk **Zakończ** do generowania szkielet aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Pochodne klasy widoków](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Alternatywy dla architektury dokument/widok](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Opcje projektowania aplikacji](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Widoki formularzy](../../mfc/form-views-mfc.md)   
 [Tworzenie aplikacji MFC w stylu Eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [Tworzenie aplikacji MFC w stylu przeglądarki sieci Web](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

