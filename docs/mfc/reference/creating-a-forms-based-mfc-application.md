---
title: Tworzenie aplikacji MFC opartej na formularzach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcforms.project
dev_langs:
- C++
helpviewer_keywords:
- applications [MFC], forms-based
- forms-based applications [MFC]
ms.assetid: 048d2f7d-b60d-4386-ad8e-71d49af9c05e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 292e3d5b0fdc7e42bd44e6993535cd176e877ca5
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/05/2018
ms.locfileid: "37851642"
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
  
1.  Postępuj zgodnie z instrukcjami [tworzenie aplikacji MFC](../../mfc/reference/creating-an-mfc-application.md).  
  
2.  W Kreatorze aplikacji MFC [typ aplikacji](../../mfc/reference/application-type-mfc-application-wizard.md) wybierz opcję **Obsługa architektury dokument/widok** pole wyboru.  
  
3.  Wybierz **pojedynczego dokumentu**, **wiele dokumentów**, lub **wiele dokumentów najwyższego poziomu**.  
  
    > [!NOTE]
    >  W przypadku wybrania SDI, MDI lub obsługi aplikacji interfejsu wielu dokumentów najwyższego poziomu, domyślnie `CView` jest ustawiony jako klasę bazową widoku aplikacji w [wygenerowane klasy](../../mfc/reference/generated-classes-mfc-application-wizard.md) strony kreatora. Aby utworzyć aplikację opartą na formularzach, jako klasę bazową widoku aplikacji należy wybrać klasę `CFormView`. Kreator nie zapewnia funkcji drukowania dla aplikacji opartej na formularzach.  
  
4.  Na pozostałych stronach kreatora skonfiguruj inne opcje projektu.  
  
5.  Kliknij przycisk **Zakończ** do zostanie wygenerowany szkielet aplikacji.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Pochodne klasy widoków](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Alternatywy dla architektury dokument/widok](../../mfc/alternatives-to-the-document-view-architecture.md)  
  
-   [Opcje do wyboru przy projektowaniu aplikacji](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kreator aplikacji MFC](../../mfc/reference/mfc-application-wizard.md)   
 [Widoki formularzy](../../mfc/form-views-mfc.md)   
 [Tworzenie aplikacji MFC w stylu Eksploratora plików](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)   
 [Tworzenie aplikacji MFC w stylu przeglądarki internetowej](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

