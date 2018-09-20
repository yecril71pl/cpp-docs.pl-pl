---
title: 'Kontrolki ActiveX MFC: Tworzenie podklasy kontrolki Windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
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
ms.openlocfilehash: 94b989594316f2eac3e65fad2cb5bf419e7ee2eb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407548"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Kontrolki ActiveX MFC: tworzenie podklasy kontrolki okna

W tym artykule opisano proces Tworzenie podklasy kontrolki Windows wspólnego, aby utworzyć formant ActiveX. Tworzenie podklasy Windows istniejący formant jest możliwość szybkiego tworzenia formantu ActiveX. Nowy formant mają możliwości formantów będących podklasami Windows, takich jak malowanie i odpowiadanie na kliknięcia myszą. Przykładowe kontrolki MFC ActiveX [przycisk](../visual-cpp-samples.md) jest przykładem Tworzenie podklasy kontrolki Windows.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).

Aby podklasy kontrolki Windows wykonaj następujące zadania:

- [Zastąp IsSubclassedControl i precreatewindow — funkcje Członkowskie COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modyfikowanie OnDraw funkcji składowej](#_core_modifying_the_ondraw_member_function)

- [Obsługa komunikaty kontrolki ActiveX (OCM) zostaną uwzględnione do kontrolki](#_core_handling_reflected_window_messages)

    > [!NOTE]
    >  Znaczną część tej pracy jest wykonywane przez kreatora kontrolek ActiveX po wybraniu kontrolki do odziedziczenia przy użyciu **wybierz klasę okna nadrzędnego** listy rozwijanej na **ustawienia kontroli** strony.

Zobacz artykuł bazy wiedzy Q243454 Aby uzyskać więcej informacji na tworzenie podklasy kontrolki.

##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Zastępowanie IsSubclassedControl i precreatewindow —

Aby zastąpić `PreCreateWindow` i `IsSubclassedControl`, Dodaj następujące wiersze kodu w celu **chronione** część deklaracji klasy kontrolki:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

W pliku implementacji (. CPP) dodaj następujące wiersze kodu, aby zaimplementować te dwie funkcje zgodnym z przesłoniętą:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Zwróć uwagę, że w tym przykładzie Windows kontrolka przycisku jest określona w `PreCreateWindow`. Jednak żadnych standardowych kontrolek Windows można być podklasą klasy. Aby uzyskać więcej informacji na temat standardowych kontrolek Windows, zobacz [formantów](../mfc/controls-mfc.md).

Tworzenie podklasy kontrolki Windows, można określić stylu określonego okna (WS_) lub rozszerzone okno flagi stylu (WS_EX_) do użycia podczas tworzenia okna formantu. Można ustawić wartości tych parametrów w `PreCreateWindow` funkcja elementu członkowskiego, modyfikując `cs.style` i `cs.dwExStyle` struktury pola. Zmiany w tych polach należy wprowadzać za pomocą **lub** operacji, aby zachować domyślne flagi, które są ustawione przez klasę `COleControl`. Na przykład, jeśli kontrolka jest tworzenie podklasy kontrolki przycisku i formant do wyświetlania jako pole wyboru, Wstaw następujący wiersz kodu do wykonania `CSampleCtrl::PreCreateWindow`, przed instrukcją return:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Ta operacja spowoduje dodanie BS_CHECKBOX Flaga style, przy równoczesnym zachowaniu flagi styl domyślny (WS_CHILD) klasy `COleControl` bez zmian.

##  <a name="_core_modifying_the_ondraw_member_function"></a> Modyfikowanie OnDraw składowa

Jeśli chcesz, aby Twoje formantów będących podklasami, aby zachować wyglądać inaczej, niż odpowiedni formant Windows `OnDraw` funkcja elementu członkowskiego dla kontrolki powinien zawierać jedynie po wywołaniu `DoSuperclassPaint` funkcji członkowskiej, jak w poniższym przykładzie:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

`DoSuperclassPaint` Funkcji członkowskiej, implementowany przez `COleControl`, używa procedurę okna kontrolki Windows narysuj kontrolkę w kontekście określonego urządzenia, w ramach prostokąt otaczający. To sprawia, że kontrolka widoczny nawet wtedy, gdy nie jest aktywny.

> [!NOTE]
>  `DoSuperclassPaint` Funkcja elementu członkowskiego będzie działać tylko w przypadku tych typów kontroli, które umożliwiają kontekstu urządzenia, które zostaną przekazane jako *wParam* z komunikat WM_PAINT. W tym niektóre standardowe kontrolek Windows, takie jak pasek PRZEWIJANIA i przycisk i wspólnych formantów. Dla formantów, które nie obsługują tego zachowania będzie musiał podać kod do prawidłowego wyświetlenia kontrolkę, która jest nieaktywny.

##  <a name="_core_handling_reflected_window_messages"></a> Obsługa odbitych komunikatów okien

Formanty Windows zazwyczaj wysyłać niektóre okna do ich nadrzędnego okna. Niektóre z tych wiadomości, takich jak WM_COMMAND, oferują powiadomienie o akcji przez użytkownika. Inne, takie jak wm_ctlcolor —, są używane do uzyskania informacji z okna nadrzędnego. Kontrolki ActiveX komunikuje się zazwyczaj z okna nadrzędnego w inny sposób. Powiadomienia są przekazywane przez wyzwalanie zdarzeń (wysyłanie powiadomień o zdarzeniach), a informacje o kontenerze kontrolki są uzyskiwane, uzyskując dostęp do właściwości otaczających kontenera. Ponieważ istnieje tych metod komunikacji, kontenery kontrolek ActiveX nie oczekuje się przetworzyć wszystkie komunikaty okna wysyłany przez kontrolkę.

Aby uniemożliwić kontenera odbieranie komunikatów okien wysyłany przez kontrolkę Windows będące podklasami `COleControl` tworzy dodatkowe okna, która będzie służyć jako element nadrzędny kontrolki. Ten dodatkowy, o nazwie "odblaskowego", jest tworzone tylko dla formantu ActiveX, że podklasy Windows kontroli i ma ten sam rozmiar i położenie okna kontrolki. W oknie odblaskowego przechwytuje niektórych komunikatów okien i wysyła je do formantu. Kontrolki w jego procedurę okna następnie może przetwarzać te komunikaty odbite poprzez wykonanie czynności odpowiednie dla formantu ActiveX (na przykład wyzwalanie zdarzenia). Zobacz [odzwierciedlone identyfikatory komunikatów okien](../mfc/reflected-window-message-ids.md) listę windows przechwycone komunikaty i odpowiadające im komunikatów odbitych.

Kontener formantu ActiveX mogą być przeznaczone do wykonywania odbicie komunikatu, eliminując konieczność łączenia się `COleControl` do tworzenia okna reflektor i skrócenia czasu wykonywania w czasie formantów będących podklasami Windows. `COleControl` wykrywa, czy kontener obsługuje tę możliwość, sprawdzając właściwości otoczenia MessageReflect o wartości **TRUE**.

Do obsługi komunikatów odbitych okna, Dodaj wpis do kontrolki mapy wiadomości i wykonywania funkcji obsługi. Ponieważ komunikaty odbite nie są częścią zestawu standardowych komunikatów zdefiniowany przez Windows, w widoku klas nie obsługuje dodawania takie programy obsługi komunikatów. Jednak nie jest trudne ręcznie dodać program obsługi.

Aby dodać program obsługi komunikatów dla komunikatów odbitych okna ręcznie wykonaj następujące czynności:

- W klasie kontrolki. Plik H deklarowanie funkcji obsługi. Funkcja powinna mieć typ zwracany **LRESULT** i dwa parametry, z typami **WPARAM** i **LPARAM**, odpowiednio. Na przykład:

     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- W klasie kontrolki. CPP plików, Dodaj odpowiedni wpis ON_MESSAGE mapie komunikatów. Parametry tego wpisu należy identyfikator wiadomości oraz nazwa funkcji programu obsługi. Na przykład:

     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- Również w. Plik CPP zaimplementować `OnOcmCommand` funkcja elementu członkowskiego do przetwarzania komunikatów odbitych. *WParam* i *lParam* parametry są takie same jak oryginalne komunikatów okien.

Przykładowy sposób uwzględnione, komunikaty są przetwarzane, znaleźć przykładowe kontrolki MFC ActiveX [przycisk](../visual-cpp-samples.md). Pokazuje `OnOcmCommand` program obsługi, który wykrywa BN_CLICKED kod powiadomienia i odpowiada wyzwalania (wysyłającym) `Click` zdarzeń.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

