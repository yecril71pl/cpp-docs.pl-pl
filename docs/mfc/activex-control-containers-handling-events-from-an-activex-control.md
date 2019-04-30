---
title: 'Kontenery kontrolek ActiveX: Obsługa zdarzeń z kontrolki ActiveX'
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
ms.openlocfilehash: 8087d84d2203e4f910200acdd1b00e58d14f920e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394900"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Kontenery kontrolek ActiveX: Obsługa zdarzeń z kontrolki ActiveX

W tym artykule omówiono, aby zainstalować programy obsługi zdarzeń dla kontrolek ActiveX w kontenerze kontrolek ActiveX przy użyciu okna właściwości. Programy obsługi zdarzeń są używane do odbierania powiadomień (z formantu) określonych zdarzeń i wykonanie akcji w odpowiedzi. To powiadomienie jest nazywany "wyzwoleniem" zdarzenia.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

> [!NOTE]
>  W tym artykule używany jest oparta na oknach dialogowych ActiveX kontroli kontenera projektu o nazwie kontener i osadzonego formantu o nazwie OK przykładowe w procedurach i kodu.

W oknie dialogowym właściwości, za pomocą przycisku zdarzenia, można utworzyć mapę zdarzeń, które mogą wystąpić w Twojej aplikacji kontenera kontrolek ActiveX. Ta mapa o nazwie "sink mapę zdarzeń,'' jest tworzone i konserwowane przez Visual C++, po dodaniu obsługi zdarzeń do klasy kontenera kontrolki. Każdy program obsługi zdarzeń, implementowane za pomocą wpisu mapy zdarzenia mapuje określonego zdarzenia funkcji elementu członkowskiego kontenera procedury obsługi zdarzeń. Ta funkcja obsługi zdarzenia jest wywoływana, gdy określone zdarzenie jest wywoływane przez obiekt formantu ActiveX.

Aby uzyskać więcej informacji na temat mapy wychwytywania zdarzeń, zobacz [mapy wychwytywania zdarzeń](../mfc/reference/event-sink-maps.md) w *odwołanie do biblioteki klas*.

##  <a name="_core_event_handler_modifications_to_the_project"></a> Modyfikacje programu obsługi zdarzeń do projektu

Korzystając z okna właściwości można dodać procedury obsługi zdarzeń, mapę ujścia zdarzeń jest zadeklarowana i zdefiniowana w projekcie. Poniższe instrukcje są dodawane do formantu. Plik CPP po raz pierwszy zostanie dodany do obsługi zdarzeń. Ten kod deklaruje mapą obiekt sink zdarzenia dla klasy okno dialogowe (w tym przypadku `CContainerDlg`):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Podczas dodawania zdarzenia przy użyciu okna właściwości, zdarzenia mapy wpis (`ON_EVENT`) zostanie dodany do mapy obiektu sink zdarzenia i procedury obsługi zdarzeń funkcji zostanie dodany do wdrożenia kontenera (. Plik CPP).

Poniższy przykład deklaruje procedurę obsługi zdarzeń, o nazwie `OnClickInCircCtrl`, dla formantu OK `ClickIn` zdarzeń:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Ponadto następujący szablon zostanie dodany do `CContainerDlg` Implementacja klasy (. Plik CPP) dla funkcji członkowskiej procedury obsługi zdarzeń:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Aby uzyskać więcej informacji na temat makr ujścia zdarzeń, zobacz [mapy wychwytywania zdarzeń](../mfc/reference/event-sink-maps.md) w *odwołanie do biblioteki klas*.

#### <a name="to-create-an-event-handler-function"></a>Aby utworzyć funkcję obsługi zdarzenia

1. Widok klasy zaznacz klasy okien dialogowych, który zawiera formant ActiveX. W tym przykładzie użyj `CContainerDlg`.

1. W oknie dialogowym właściwości kliknij **zdarzenia** przycisku.

1. W oknie dialogowym właściwości wybierz identyfikator formantu osadzonego formantu ActiveX. W tym przykładzie użyj `IDC_CIRCCTRL1`.

   Okno właściwości wyświetla listę zdarzeń, które mogą być wywoływane przez osadzonego formantu ActiveX. Żadnej funkcji składowej pogrubione już ma funkcje obsługi do niej przypisany.

1. Wybierz zdarzenie ma klasy okien dialogowych, aby obsłużyć. W tym przykładzie wybierz **kliknij**.

1. W polu listy rozwijanej po prawej stronie wybierz  **\<Dodaj > ClickCircctrl1**.

1. Kliknij dwukrotnie przycisk Nowa funkcja obsługi z widoku klasy, aby przejść do kodu programu obsługi zdarzeń w implementacji (. Plik CPP) `CContainerDlg`.

## <a name="see-also"></a>Zobacz także

[Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)
