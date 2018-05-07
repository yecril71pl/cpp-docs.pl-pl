---
title: 'Kontenery formantów ActiveX: Programowanie formantów ActiveX w kontenerze formantów ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC], accessing ActiveX controls
- Confirm Classes dialog box
- wrapper classes [MFC], ActiveX controls
- ActiveX control containers [MFC], wrapper classes
- ActiveX controls [MFC], accessing
- MFC ActiveX controls [MFC], accessing in containers
- header files [MFC], for ActiveX control wrapper class
- wrapper classes [MFC], using
- ActiveX controls [MFC], wrapper classes
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bae926cfc7e83edeef9ee68c7ce7118c55009a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="activex-control-containers-programming-activex-controls-in-an-activex-control-container"></a>Kontenery kontrolek ActiveX: programowanie kontrolek ActiveX w kontenerze kontrolek ActiveX
W tym artykule opisano proces do uzyskiwania dostępu do narażonych [metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md) osadzonych formantów ActiveX. Zasadniczo spowoduje wykonaj następujące kroki:  
  
1.  [Wstawianie formantu ActiveX w projekcie kontenera ActiveX](../mfc/inserting-a-control-into-a-control-container-application.md) za pomocą galerii.  
  
2.  [Zdefiniuj zmienną członkowską](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) (lub inne formy dostępu) z tego samego typu co ActiveX kontrolować klasy otoki.  
  
3.  [Kontrolki ActiveX programu](#_core_programming_the_activex_control) przy użyciu wstępnie zdefiniowanych funkcji elementów członkowskich klasy otoki.  
  
 Dla tej dyskusji przyjęto założenie, że po utworzeniu projektu opartych na oknach dialogowych (o nazwie kontenera) z obsługą formantu ActiveX. Formantu próbki OK OK, zostaną dodane do Projekt wynikowy.  
  
 Po kontroli OK zostaną wstawione do projektu (krok 1), włóż wystąpienia formantu OK do głównego okna dialogowego aplikacji.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-add-the-circ-control-to-the-dialog-template"></a>Aby dodać kontrolki OK do szablonu okna dialogowego  
  
1.  Załaduj projekt kontenera formantu ActiveX. Na przykład użyć `Container` projektu.  
  
2.  Na karcie Widok zasobów.  
  
3.  Otwórz **okna dialogowego** folderu.  
  
4.  Kliknij dwukrotnie szablon okno główne okno dialogowe. Na przykład użyć **IDD_CONTAINER_DIALOG**.  
  
5.  Kliknij ikonę kontroli OK w przyborniku.  
  
6.  Kliknij punkt, w oknie dialogowym Wstaw formant OK.  
  
7.  Z **pliku** menu, wybierz **Zapisz wszystko** można zapisać wszystkich zmian do szablonu — okno dialogowe.  
  
## <a name="modifications-to-the-project"></a>Zmiany do projektu  
 Aby włączyć OK kontroli dostępu do aplikacji kontenera, Visual C++ automatycznie dodaje klasy otoki (`CCirc`) pliku implementacji (. CPP) do projektu kontenera i nagłówka klasy otoki (. H) pliku do pliku nagłówka okno dialogowe:  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a> Nagłówka klasy otoki (. H) plik  
 Pobierz i ustaw właściwości (i wywołania metod) dla formantu OK `CCirc` klasy otoki zawiera deklarację narażonych wszystkie metody i właściwości. W tym przykładzie deklaracji znajdują się w okólnik H. Poniższy przykład jest częścią klasy `CCirc` definiuje interfejsów formantu ActiveX:  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 Następnie można wywołać funkcji z innych procedur aplikacji przy użyciu normalnego składni języka C++. Aby uzyskać więcej informacji na temat używania tej funkcji Członkowskich ustawić dostęp do metody i właściwości formantu, zobacz sekcję [programowania formantu ActiveX](#_core_programming_the_activex_control).  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a> Modyfikacje zmiennej elementu członkowskiego do projektu  
 Gdy formant ActiveX został dodany do projektu i osadzone w kontenerze — okno dialogowe, jest dostępny przez inne części projektu. Najprostszym sposobem kontroli dostępu jest [Utwórz zmienną członkowską](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) klasy okna dialogowego `CContainerDlg` (krok 2), czyli z tego samego typu co klasy otoki dodane do projektu w programie Visual C++. Można następnie użyć zmiennej członkowskiej do formantu osadzonego w dowolnym momencie.  
  
 Gdy **Dodawanie zmiennej członkowskiej** dodaje okno dialogowe `m_circctl` elementu członkowskiego zmiennej do projektu, dodane również następujące wiersze do pliku nagłówka (. H) z `CContainerDlg` klasy:  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 Ponadto wywołanie **ddx_control —** jest automatycznie dodawany do `CContainerDlg`w implementacji `DoDataExchange`:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a> Programowania formantu ActiveX  
 W tym momencie zostały wstawione do szablonu okna dialogowego formantu ActiveX i utworzonej dla niego zmienną członkowską. Typowe składni języka C++ umożliwia teraz dostęp do właściwości i metod formantu osadzonego.  
  
 Jak wspomniano (w [nagłówka klasy otoki (. H) pliku](#_core_the_wrapper_class_header_28h29_file)), plik nagłówka (. H) dla `CCirc` klasy otoki, w tym okólnik wielkość H, zawiera listę funkcji elementów członkowskich, które służą do pobierania i ustawiania wartości właściwości uwidocznione. Dostępne są również funkcje Członkowskie dla metod uwidocznione.  
  
 Modyfikowanie właściwości formantu spójne znajduje się w `OnInitDialog` funkcji członkowskiej klasy głównym oknie dialogowym. Ta funkcja jest wywoływana bezpośrednio przed zamknięciem okna dialogowego zostanie wyświetlony i służy do inicjowania jego zawartość, łącznie z dowolnego z jego formantów.  
  
 Poniższy przykład kodu wykorzystuje `m_circctl` zmiennej członkowskiej, aby zmodyfikować właściwości podpisu i CircleShape osadzonego formantu OK:  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/cpp/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

