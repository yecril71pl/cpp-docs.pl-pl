---
title: 'Formanty MFC ActiveX: Tworzenie podklasy kontrolki okna | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- precreatewindow
- IsSubclassed
dev_langs:
- C++
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 95d6109bdc6ae28b748ee0be78e14ab62bba10fd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355440"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Kontrolki ActiveX MFC: tworzenie podklasy kontrolki okna
W tym artykule opisano proces Tworzenie podklasy formantu wspólnego systemu Windows można utworzyć formantu ActiveX. Tworzenie podklas istniejącymi systemu Windows formant jest szybkie opracowywanie formantu ActiveX. Nowe kontrolka będzie miała możliwości podklasą kontrolki systemu Windows, takich jak malowanie i odpowiadanie na kliknięcia myszą. Przykładowe kontrolki MFC ActiveX [przycisk](../visual-cpp-samples.md) przykładem Tworzenie podklasy kontrolki systemu Windows.  
  
 Aby podklasą kontrolki systemu Windows należy wykonać następujące zadania:  
  
-   [Funkcje Członkowskie IsSubclassedControl i PreCreateWindow colecontrol — zastąpienie](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [Modyfikowanie OnDraw funkcji członkowskiej](#_core_modifying_the_ondraw_member_function)  
  
-   [Obsługa komunikaty formantu ActiveX (OCM) odzwierciedlana formantu](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  Znaczną część tej pracy odbywa się automatycznie przez Kreator kontrolek ActiveX w przypadku wybrania formantu do odziedziczenia przy użyciu **wybierz klasę okna nadrzędnego** listy rozwijanej na **ustawienia kontroli** strony.  
  
 Zobacz artykuł bazy wiedzy Knowledge Base Q243454, aby uzyskać więcej informacji na tworzenie podklasy formantu.  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Zastępowanie IsSubclassedControl i PreCreateWindow  
 Aby zastąpić `PreCreateWindow` i `IsSubclassedControl`, Dodaj następujące wiersze kodu do `protected` sekcji deklaracji klasy formantu:  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 W pliku implementacji (. CPP) dodaj następujące wiersze kodu do wykonania dwóch przesłoniętej funkcji:  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 Powiadomienie, że w tym przykładzie systemu Windows przycisk formantu jest określona w `PreCreateWindow`. Można jednak odziedziczenia wszystkie formanty standardowe systemu Windows. Aby uzyskać więcej informacji dotyczących formantów standardowych systemu Windows, zobacz [formanty](../mfc/controls-mfc.md).  
  
 Podczas tworzenie podklasy kontrolki systemu Windows, może być określenie stylu poszczególnego okna (**WS_**) lub rozszerzone style okna (**WS_EX_**) flagi ma być używany podczas tworzenia okna formantu. Można ustawić wartości dla parametrów w `PreCreateWindow` funkcji członkowskiej, modyfikując **cs.style** i **cs.dwExStyle** struktury pól. Zmiany w tych polach należy wprowadzać za pomocą `OR` operacji, aby zachować domyślnych flag, które są ustawiane przez klasę `COleControl`. Na przykład, jeśli formant jest tworzenie podklasy formantu przycisku i chcesz formantu ma postać pola wyboru, Wstaw następujący wiersz kodu do wykonania `CSampleCtrl::PreCreateWindow`, przed instrukcji return:  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 Ta operacja doda **bs_checkbox —** styl flagi, pozostawiając flagi styl domyślny (**ws_child —**) klasy `COleControl` bez zmian.  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a> Modyfikowanie funkcji członkowskiej OnDraw  
 Jeśli chcesz, aby podklasą formantu do zachowania wyglądać inaczej, niż odpowiedniego formantu Windows `OnDraw` funkcji członkowskiej formantu powinna zawierać tylko wywołania `DoSuperclassPaint` funkcji członkowskiej, jak w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 `DoSuperclassPaint` Funkcji członkowskiej, implementowane przez `COleControl`, używa procedurę okna kontrolki Windows, by narysować kontrolkę w kontekście określonego urządzenia, w ramach prostokątem. Dzięki temu formantu widoczne nawet wtedy, gdy nie jest aktywny.  
  
> [!NOTE]
>  `DoSuperclassPaint` Funkcji członkowskiej będzie działać tylko z tych typów kontroli, umożliwiających kontekstu urządzenia mają być przekazywane jako **wParam** z `WM_PAINT` wiadomości. Obejmuje to niektóre formanty standardowe systemu Windows, takich jak **pasek PRZEWIJANIA** i **przycisk**i formanty standardowe. Dla formantów, które nie obsługują tego zachowania należy podać kod do prawidłowego wyświetlenia kontrolkę, która jest nieaktywne.  
  
##  <a name="_core_handling_reflected_window_messages"></a> Obsługa odbitych komunikatów okien  
 Formanty systemu Windows zwykle wysyłać komunikatów okna do ich okno nadrzędne. Niektóre z tych wiadomości, takie jak **WM_COMMAND**, podaj powiadomień akcji przez użytkownika. Inne, takie jak `WM_CTLCOLOR`, są używane do uzyskania informacji z okna nadrzędnego. Kontrolki ActiveX zazwyczaj komunikuje się z okna nadrzędnego w inny sposób. Powiadomienia są przekazywane przez wyzwalania zdarzenia (wysyłanie powiadomień o zdarzeniach), a informacje o kontenerze formant uzyskuje się poprzez podczas uzyskiwania dostępu do właściwości otaczających kontenera. Ponieważ te techniki komunikacji istnieje, nie powinny kontenery formantów ActiveX do przetworzenia okna wiadomości wysyłanych przez formant.  
  
 Aby uniemożliwić kontenera odbieranie komunikatów okien wysyłany przez kontrolkę podklasą Windows `COleControl` tworzy dodatkowe okno jako element nadrzędny kontrolki. To dodatkowe okna o nazwie "reflektora", jest tworzony tylko dla formantu ActiveX, że podklasy systemu Windows kontroli i ma rozmiar i położenie okna formantu. Okno reflektora przechwytuje niektórych komunikatów okien i wysyła je z powrotem do formantu. Kontrolki, w jego procedurę okna następnie może przetwarzać te komunikaty odbite przez podejmowanie działań odpowiednich dla formantu ActiveX (na przykład zdarzenie). Zobacz [odzwierciedlone identyfikatory komunikatów okien](../mfc/reflected-window-message-ids.md) listę przechwycone windows wiadomości i odpowiednie komunikatów odbitych.  
  
 Kontenera kontrolki ActiveX mogą służyć do odbicie wiadomości, eliminując konieczność `COleControl` można utworzyć okna reflektora i zmniejszenia czasu wykonywania w czasie podklasą kontrolki systemu Windows. `COleControl` wykrywa, czy kontener obsługuje tę możliwość przez sprawdzenie właściwości otoczenia MessageReflect o wartości **TRUE**.  
  
 Obsługa komunikatów odbitych okna, Dodaj wpis do mapy formantów wiadomości i implementacji funkcji obsługi. Ponieważ komunikaty odbite nie są częścią standardowy zestaw komunikatów zdefiniowanych w systemie Windows, Widok klas nie obsługuje dodawania takie programy obsługi wiadomości. Jednak nie jest trudne ręcznie dodać program obsługi.  
  
 Aby dodać program obsługi komunikatów dla komunikatów odbitych okna ręcznie wykonaj następujące czynności:  
  
-   Klasy formantu. Plik H zadeklarowania funkcji programu obsługi. Funkcja powinien mieć typ zwracany **elementu LRESULT** i dwa parametry o typach **WPARAM** i **LPARAM**odpowiednio. Na przykład:  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   Klasy formantu. CPP plików, dodawanie `ON_MESSAGE` wpisu mapy komunikatów. Parametry ten wpis musi być identyfikator wiadomości i nazwa funkcji programu obsługi. Na przykład:  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   Również w. Pliku CPP zaimplementować **OnOcmCommand** funkcji członkowskiej do przetwarzania komunikatów odbitych. **WParam** i **lParam** parametry są takie same jak oryginalne komunikatów okien.  
  
 Na przykład uwzględniane komunikaty są przetwarzane, dotyczą próbka formantów MFC ActiveX [przycisk](../visual-cpp-samples.md). Przedstawia on **OnOcmCommand** obsługi, która wykrywa **BN_CLICKED** kod powiadomienia i zdarzenie Click odpowiada za uruchamiania (wysyłającym).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

