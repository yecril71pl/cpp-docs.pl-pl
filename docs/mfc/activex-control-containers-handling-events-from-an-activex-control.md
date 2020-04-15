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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367951"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Kontenery kontrolek ActiveX: obsługa zdarzeń z kontrolki ActiveX

W tym artykule omówiono użycie okna **Właściwości** (w **widoku klasy)** do instalowania programów obsługi zdarzeń dla formantów ActiveX w kontenerze formantu ActiveX. Programy obsługi zdarzeń są używane do odbierania powiadomień (z formantu) niektórych zdarzeń i wykonywania niektórych akcji w odpowiedzi. To powiadomienie jest nazywane "wypalanie" zdarzenia.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

> [!NOTE]
> W tym artykule użyto opartego na oknie dialogowym projektu kontenera formantu ActiveX o nazwie Kontener i osadzonego formantu o nazwie Circ jako przykłady w procedurach i kodzie.

Za pomocą przycisku Zdarzenia w oknie **Właściwości** (w **widoku klasy)** można utworzyć mapę zdarzeń, które mogą wystąpić w aplikacji kontenera sterowania ActiveX. Ta mapa, o nazwie "mapa ujścia zdarzeń", jest tworzony i obsługiwany przez visual C++ po dodaniu programów obsługi zdarzeń do klasy kontenera formantu. Każdy program obsługi zdarzeń, zaimplementowany z wpisem mapy zdarzeń, mapuje określone zdarzenie na funkcję elementów członkowskich obsługi zdarzeń kontenera. Ta funkcja obsługi zdarzeń jest wywoływana, gdy określone zdarzenie jest uruchamiane przez obiekt kontrolny ActiveX.

Aby uzyskać więcej informacji na temat map ujścia zdarzeń, zobacz [Mapy ujścia zdarzeń](../mfc/reference/event-sink-maps.md) w *odwołaniu do biblioteki klas*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Modyfikacje programu obsługi zdarzeń w projekcie

Podczas korzystania z **właściwości** okna, aby dodać programy obsługi zdarzeń, mapa ujścia zdarzeń jest zadeklarowany i zdefiniowany w projekcie. Następujące instrukcje są dodawane do formantu . CPP po raz pierwszy dodano program obsługi zdarzeń. Ten kod deklaruje mapę ujścia zdarzeń dla klasy `CContainerDlg`okna dialogowego (w tym przypadku):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

W miarę **Properties** dodawania zdarzeń za pomocą okna`ON_EVENT`Właściwości dodawania zdarzeń do mapy zdarzeń ( ) jest dodawany do mapy ujścia zdarzeń, a funkcja obsługi zdarzeń jest dodawana do implementacji kontenera (. CPP).

Poniższy przykład deklaruje program obsługi `OnClickInCircCtrl`zdarzeń, wywoływany dla `ClickIn` zdarzenia formantu Circ:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Ponadto do implementacji `CContainerDlg` klasy jest dodawany następujący szablon (. CPP) dla funkcji elementu członkowskiego programu obsługi zdarzeń:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Aby uzyskać więcej informacji na temat makr ujścia zdarzeń, zobacz [Mapy ujścia zdarzeń](../mfc/reference/event-sink-maps.md) w *odwołaniu do biblioteki klas*.

#### <a name="to-create-an-event-handler-function"></a>Aby utworzyć funkcję obsługi zdarzeń

1. W widoku klasy wybierz klasę okna dialogowego zawierającą kontrolka ActiveX. W tym przykładzie użyj programu `CContainerDlg`.

1. W oknie **Właściwości** kliknij przycisk **Zdarzenia.**

1. W oknie **Właściwości** wybierz identyfikator formantu osadzonego formantu ActiveX. W tym przykładzie użyj programu `IDC_CIRCCTRL1`.

   Okno **Właściwości** wyświetla listę zdarzeń, które mogą być uruchamiane przez osadzony formant ActiveX. Każda funkcja elementu członkowskiego pokazana pogrubioną czcionką ma już przypisane funkcje obsługi.

1. Wybierz zdarzenie, które ma obsługiwać klasa okna dialogowego. W tym przykładzie wybierz pozycję **Kliknij**.

1. Z listy rozwijanej po prawej stronie wybierz pozycję ** \<Dodaj> Kliknij przycisk Kliknij przyciskU Kliknij przyciskU Kliknij przycisku Kliknij przyciskU Kliknij przycisku Kliknij przycisku Kliknij przycisku Kliknij przycisku Kliknij przycisk>.**

1. Kliknij dwukrotnie nową funkcję obsługi z widoku klasy, aby przejść do kodu obsługi zdarzeń w implementacji (. CPP) z `CContainerDlg`pliku .

## <a name="see-also"></a>Zobacz też

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
