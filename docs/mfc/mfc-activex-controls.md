---
title: Formanty MFC ActiveX | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c06b66be2dd9b982fc925aa69483a58fcc4799dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls"></a>Kontrolki ActiveX MFC
Formant ActiveX jest składnik oprogramowania wielokrotnego użytku, oparte na modelu obiektu składników (COM), obsługuje wiele funkcji OLE, który można dostosować do potrzeb wiele oprogramowania. Formanty ActiveX są przeznaczone do użycia zarówno w zwykłym kontenery formantów ActiveX w Internecie, w strony sieci Web. Formanty ActiveX można utworzyć za pomocą MFC, opisane w tym miejscu lub z [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).  
  
 Formant ActiveX jest narysowanie sam w osobnym oknie, odpowiadanie na zdarzenia (takie jak kliknięcie myszą), a następnie można zarządzać za pomocą interfejsu, który zawiera właściwości i metody podobne do obiektów automatyzacji.  
  
 Formanty te mogą być opracowane dla wielu zastosowań, takich jak dostęp do bazy danych, monitorowania i tworzenie wykresów danych. Oprócz ich przenośność formantów ActiveX obsługuje funkcje wcześniej dostępne do formantu ActiveX, takich jak zgodność z istniejącą kontenery OLE i możliwość integracji z menu kontenera OLE ich menu. Ponadto formantu ActiveX w pełni obsługuje automatyzację, co umożliwia sterowanie do udostępnienia właściwości odczytem/zapisem i zestaw metod, które mogą być wywoływane przez kontrolki użytkownika.  
  
 Można utworzyć formanty ActiveX niepowiązane z oknami i kontrolek, które tylko utworzyć okna, gdy stanie się aktywne. Formanty bez okien przyspieszyć wyświetlanie aplikacji i umożliwia przezroczyste i nieprostokątny formantów. Można również asynchronicznie ładować właściwości formantu ActiveX.  
  
 Formant ActiveX jest wdrażany jako serwer w procesie (zazwyczaj małego obiektu) używanej w dowolnym kontener OLE. Należy pamiętać, że wszystkie funkcje formantu ActiveX dostępne tylko wtedy, gdy jest używany w kontenerze OLE zaprojektowane pod uwagę formantów ActiveX. Zobacz [portu formantów ActiveX do innych aplikacji](../mfc/containers-for-activex-controls.md) listę kontenerach obsługujących formanty ActiveX. Tego typu kontenera, zwany "kontenera formantu" może działać formantu ActiveX przy użyciu właściwości i metod formantu i odbierania powiadomień z formantu ActiveX w formularzu zdarzenia. Na poniższym rysunku pokazano interakcji.  
  
 ![Wzajemne oddziaływanie kontenera formantu ActiveX i kontroli](../mfc/media/vc37221.gif "vc37221")  
Interakcja między kontenerze formantów ActiveX i okna formantu ActiveX  
  
 Niektóre najnowsze informacje dotyczące optymalizacji formantów ActiveX, zobacz [kontrolki ActiveX MFC: Optymalizacja](../mfc/mfc-activex-controls-optimization.md).  
  
 Aby utworzyć formantu MFC ActiveX, zobacz [Tworzenie projektu formantu ActiveX](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)  
  
-   [Dokumenty aktywne](../mfc/active-documents.md)  
  
-   [Opis ActiveX — formanty](http://msdn.microsoft.com/library/windows/desktop/ms693753)  
  
-   [Uaktualnianie istniejącego formantu ActiveX do użycia w Internecie](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a>Podstawowe składniki formantu ActiveX  
 Kontrolki ActiveX używa kilku elementów programistycznych wydajnie interakcję z kontenera formantu i użytkownika. Są to klasa [colecontrol —](../mfc/reference/colecontrol-class.md), zestaw funkcji inicjowanie zdarzeń i wysyłania mapy.  
  
 Każdy obiekt formantu ActiveX, w przypadku tworzenia dziedziczy jej klasa podstawowa MFC bogaty zestaw funkcji `COleControl`. Te funkcje obejmują Aktywacja w miejscu i logiki automatyzacji. `COleControl`te same funkcje co obiekt window MFC, a także możliwość wyzwalać zdarzeń można udostępnić obiektu formantu. `COleControl`można też podać [kontrolek bez okien](../mfc/providing-windowless-activation.md), które polegać na ich kontenera, aby uzyskać pomoc dotyczącą niektóre funkcje okna zapewnia (przechwytywanie myszy, klawiatury, przewijanie), ale oferuje znacznie szybsze wyświetlanie.  
  
 Ponieważ pochodną klasy formantu `COleControl`, dziedziczy możliwość wysyłania lub zdarzeń do kontenera formantu, gdy zostaną spełnione określone warunki o nazwie "fire," wiadomości. Te zdarzenia są używane do powiadomi kontenera formantu, gdy coś ważne odbywa się w formancie. Dodatkowe informacje o zdarzeniu można wysłać do kontenera formantu dołączając parametrów zdarzenia. Aby uzyskać więcej informacji na temat zdarzeń formantu ActiveX, zobacz artykuł [kontrolki ActiveX MFC: zdarzenia](../mfc/mfc-activex-controls-events.md).  
  
 Końcowy element jest mapy wysyłania, który jest używany do udostępnienia zestaw funkcji (nazywanych metody) i atrybuty (nazywane właściwości) dla użytkownika formant. Właściwości Zezwalaj kontenera kontrolki lub kontroli użytkownika do manipulowania kontrolki na różne sposoby. Użytkownik może Zmienianie wyglądu formantu, zmiany niektórych wartości formantu lub żądania kontroli, takich jak uzyskiwanie dostępu do określone dane, które obsługuje formantu. Ten interfejs jest określana przez dewelopera kontrolek i jest definiowana za pomocą **widoku klasy**. Aby uzyskać więcej informacji dotyczących właściwości i metod formantu ActiveX, zobacz artykuły [kontrolki ActiveX MFC: metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md).  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interakcja między formantami z systemem Windows i kontenery formantów ActiveX  
 Gdy formant jest używany w kontenerze kontroli, używa dwóch mechanizmów do komunikowania się: ujawnia on właściwości i metody, a jego wyzwala zdarzenia. Na poniższym rysunku pokazano implementowania tych dwóch mechanizmów.  
  
 ![Formant ActiveX, który komunikuje się z jego kontenera](../mfc/media/vc37222.gif "vc37222")  
Komunikacja między kontenerze formantów ActiveX i formantu ActiveX  
  
 Również na poprzedniej ilustracji pokazano, jak inne interfejsy OLE (oprócz automatyzacji i zdarzenia) są obsługiwane przez formanty.  
  
 Wszystkie kontrolki komunikacji z kontenerem odbywa się za pośrednictwem `COleControl`. Do obsługi niektórych żądań kontenera **colecontrol —** wywołać elementu członkowskiego funkcje, które zostały wdrożone w klasy formantu. Wszystkie metody i niektóre właściwości są obsługiwane w ten sposób. Klasa formantu można także zainicjować komunikacji z kontenerem przez wywołanie funkcji Członkowskich `COleControl`. Zdarzenia są uruchamiane w ten sposób.  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a>Stany aktywną i nieaktywną formantu ActiveX  
 Formant ma dwa stany podstawowe: aktywnych i nieaktywnych. Zazwyczaj te stany zostały rozróżnianych na podstawie tego, czy formant miał okna. Aktywny formant miał okna; nie kontrolkę, która jest nieaktywne. Ta różnica nie jest już uniwersalnych wraz z wprowadzeniem aktywacji niepowiązanej z oknami, ale nadal mają zastosowanie wielu formantów.  
  
 Gdy [kontroli bez okien](../mfc/providing-windowless-activation.md) umieszczane active wywołuje przechwytywanie myszy, klawiatury, przewijanie i innych usług okna z jego kontenera. Możesz również [Podaj interakcji z myszą do formantów nieaktywne](../mfc/providing-mouse-interaction-while-inactive.md), jak również formanty utworzone [czekać do momentu aktywowania można utworzyć okna](../mfc/turning-off-the-activate-when-visible-option.md).  
  
 Podczas aktywowania formantu z oknem jest w stanie pełni interakcję z kontenera formantu, użytkownika i systemu Windows. Na poniższej ilustracji przedstawiono ścieżki komunikacji między formantu ActiveX, kontenera formantu i systemu operacyjnego.  
  
 ![Przetwarzanie w aktywny formant ActiveX okna komunikatów](../mfc/media/vc37223.gif "vc37223")  
Przetwarzania w formancie ActiveX okna (jeśli jest aktywny) komunikatów systemu Windows  
  
##  <a name="_core_serializing_activex_elements"></a>Serializacja  
 Możliwość serializowania danych, czasami określane jako trwałości, umożliwia sterowanie do zapisu wartości właściwości do magazynu trwałego. Formanty można następnie utworzyć ponownie, odczytując stan obiektu z magazynu.  
  
 Należy pamiętać, że formant nie jest odpowiedzialny za uzyskanie dostępu do nośnika magazynowania. Zamiast tego formantu kontenera jest odpowiedzialny za zapewnienie formantu z nośnika magazynowania do użycia w odpowiednim czasie. Aby uzyskać więcej informacji na serializacji, zobacz artykuł [kontrolki ActiveX MFC: serializacja](../mfc/mfc-activex-controls-serializing.md). Aby uzyskać informacje dotyczące optymalizacji serializacji, zobacz [Optymalizacja stanu trwałego i inicjalizacji](../mfc/optimizing-persistence-and-initialization.md) w formantach ActiveX: Optymalizacja.  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a>Instalowanie narzędzia i klasy formantów ActiveX  
 Po zainstalowaniu programu Visual C++ MFC ActiveX kontrolować klasy i handlowych i debugowanie formantu ActiveX, który biblioteki DLL środowiska wykonawczego są instalowane automatycznie, jeśli nie wybrano formantów ActiveX w Instalatorze (są one wybrane domyślnie).  
  
 Domyślnie klasy formantów ActiveX i narzędzia są instalowane w następujących podkatalogów w obszarze \Program Files\Microsoft programu Visual Studio .NET:  
  
-   **\Common7\Tools**  
  
     Zawiera pliki kontenera testu (TstCon32.exe, a także jej pliki pomocy).  
  
-   **\Vc7\atlmfc\include**  
  
     Zawiera pliki nagłówkowe, konieczne jest opracowanie formantów ActiveX MFC  
  
-   **\Vc7\atlmfc\src\mfc**  
  
     Zawiera kod źródłowy dla określonej klasy formantów ActiveX w MFC  
  
-   **\Vc7\atlmfc\lib**  
  
     Zawiera biblioteki wymagane do opracowywania formantów ActiveX MFC  
  
 Istnieją również przykłady dla formantów MFC ActiveX. Aby uzyskać więcej informacji na temat te przykłady, zobacz [przykłady formantów: MFC-Based formantów ActiveX](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
