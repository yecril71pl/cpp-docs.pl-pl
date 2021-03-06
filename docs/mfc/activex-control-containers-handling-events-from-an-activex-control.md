---
title: 'Kontenery kontrolek ActiveX: obsługa zdarzeń z kontrolki ActiveX'
ms.date: 09/12/2018
helpviewer_keywords:
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
ms.openlocfilehash: 4b7bc78a2937c010a4d2f1fb000ae0fe8ca2416c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625125"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Kontenery kontrolek ActiveX: obsługa zdarzeń z kontrolki ActiveX

W tym artykule omówiono użycie okna **Właściwości** (w **Widok klasy**) w celu zainstalowania programów obsługi zdarzeń dla formantów ActiveX w kontenerze kontrolek ActiveX. Procedury obsługi zdarzeń są używane do odbierania powiadomień (z formantu) określonych zdarzeń i wykonywania niektórych akcji w odpowiedzi. To powiadomienie jest nazywane "wyzwoleniem".

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

> [!NOTE]
> W tym artykule jest stosowany oparty na oknach dialogowych projekt kontenera o nazwie Container i osadzony formant o nazwie okólnik jako przykłady w procedurach i kodzie.

Za pomocą przycisku zdarzenia w oknie **Właściwości** (w **Widok klasy**) można utworzyć mapę zdarzeń, które mogą wystąpić w aplikacji kontenera kontrolek ActiveX. Ta mapa o nazwie "Mapa ujścia zdarzeń" jest tworzona i utrzymywana przez Visual C++ po dodaniu obsługi zdarzeń do klasy kontenera formantów. Każdy program obsługi zdarzeń wdrożony przy użyciu wpisu mapy zdarzeń mapuje określone zdarzenie do funkcji członkowskiej programu obsługi zdarzeń kontenera. Ta funkcja obsługi zdarzeń jest wywoływana, gdy określone zdarzenie jest wywoływane przez obiekt kontrolki ActiveX.

Aby uzyskać więcej informacji na temat map ujścia zdarzeń, zobacz [mapy ujścia zdarzeń](reference/event-sink-maps.md) w *dokumentacji biblioteki klas*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Modyfikacje programu obsługi zdarzeń w projekcie

W przypadku dodawania obsługi zdarzeń przy użyciu okna **Właściwości** , Mapa ujścia zdarzeń jest zadeklarowana i zdefiniowana w projekcie. Następujące instrukcje są dodawane do kontrolki. Plik CPP podczas pierwszego dodawania programu obsługi zdarzeń. Ten kod deklaruje mapę ujścia zdarzeń dla klasy okna dialogowego (w tym przypadku `CContainerDlg` ):

[!code-cpp[NVC_MFC_AxCont#8](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Podczas używania okna **Właściwości** do dodawania zdarzeń, wpis mapy zdarzeń ( `ON_EVENT` ) zostanie dodany do mapy ujścia zdarzeń, a funkcja obsługi zdarzeń zostanie dodana do implementacji kontenera (. CPP).

Poniższy przykład deklaruje procedurę obsługi zdarzeń o nazwie `OnClickInCircCtrl` dla zdarzenia kontrolki cykl `ClickIn` :

[!code-cpp[NVC_MFC_AxCont#10](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Ponadto do implementacji klasy zostanie dodany następujący szablon `CContainerDlg` (. CPP) dla funkcji składowej programu obsługi zdarzeń:

[!code-cpp[NVC_MFC_AxCont#11](codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Aby uzyskać więcej informacji na temat makr ujścia zdarzeń, zobacz [mapy ujścia zdarzeń](reference/event-sink-maps.md) w *dokumentacji biblioteki klas*.

#### <a name="to-create-an-event-handler-function"></a>Aby utworzyć funkcję programu obsługi zdarzeń

1. W obszarze Widok klasy wybierz klasę okna dialogowego, która zawiera kontrolkę ActiveX. Na potrzeby tego przykładu Użyj `CContainerDlg` .

1. W oknie **Właściwości** kliknij przycisk **zdarzenia** .

1. W oknie **Właściwości** wybierz identyfikator kontrolki osadzonej kontrolki ActiveX. Na potrzeby tego przykładu Użyj `IDC_CIRCCTRL1` .

   W oknie **Właściwości** zostanie wyświetlona lista zdarzeń, które mogą być wywoływane przez osadzony formant ActiveX. Każda funkcja członkowska pokazana w pogrubieniu ma już przypisane funkcje obsługi.

1. Wybierz zdarzenie, które ma być obsługiwane przez klasę okna dialogowego. Na potrzeby tego przykładu wybierz **pozycję kliknij**.

1. W polu listy rozwijanej po prawej stronie wybierz pozycję ** \<Add> ClickCircctrl1**.

1. Kliknij dwukrotnie nową funkcję obsługi w Widok klasy, aby przejść do kodu programu obsługi zdarzeń w implementacji (. CPP) pliku `CContainerDlg` .

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](activex-control-containers.md)
