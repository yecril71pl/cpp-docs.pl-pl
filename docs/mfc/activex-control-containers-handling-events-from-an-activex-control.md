---
title: 'Kontenery formantów ActiveX: Obsługa zdarzeń z formantu ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84e1571f400297584e12a40dfd2bfcc3c0b525d2
ms.sourcegitcommit: 0523c88b24d963c33af0529e6ba85ad2c6ee5afb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Kontenery kontrolek ActiveX: obsługa zdarzeń z kontrolki ActiveX
W tym artykule omówiono korzystanie z okna właściwości instalacji obsługi zdarzeń dla formantów ActiveX w kontenerze formantów ActiveX. Programy obsługi zdarzeń są używane do otrzymywania powiadomień (od formantu) niektórych zdarzeń i wykonanie akcji w odpowiedzi. To powiadomienie jest nazywany "wyzwoleniem" zdarzenia.  
  
> [!NOTE]
>  W tym artykule wykorzystano opartych na oknach dialogowych ActiveX formantu kontenera projektu o nazwie kontenera i osadzonego formantu o nazwie OK jako przykłady w procedurach i kod.  
  
 Za pomocą przycisku zdarzeń w oknie właściwości, można utworzyć mapę zdarzeń, które mogą wystąpić w Twojej aplikacji kontenera formantów ActiveX. Ta mapa o nazwie "sink mapę zdarzeń," nie zostanie utworzona i obsługiwanego przez Visual C++, po dodaniu obsługi zdarzeń do klasy formantu kontenera. Każdy program obsługi zdarzeń, zaimplementowany przy użyciu wpisu mapy zdarzenia mapuje określonego zdarzenia do kontenera funkcji członkowskiej programu obsługi zdarzeń. Ta funkcja obsługi zdarzeń jest wywoływane, gdy określone zdarzenie jest wywoływane przez obiekt formantu ActiveX.  
  
 Aby uzyskać więcej informacji dotyczących mapy wychwytywania zdarzeń, zobacz [mapy wychwytywania zdarzeń](../mfc/reference/event-sink-maps.md) w *informacje dotyczące biblioteki klas*.  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a> Zmiany obsługi zdarzeń do projektu  
 Korzystając z okna właściwości można dodać obsługi zdarzeń, mapa ujścia zdarzeń został zadeklarowany i zdefiniowane w projekcie. Poniższe instrukcje są dodawane do formantu. Pliku CPP program obsługi zdarzeń jest dodawany po raz pierwszy. Ten kod deklaruje mapy obiekt sink zdarzenia dla klasy okno dialogowe (w tym przypadku `CContainerDlg`):  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 Podczas dodawania zdarzenia przy użyciu okna właściwości, zdarzenia mapowania wpis (`ON_EVENT`) zostanie dodany do mapy obiekt sink zdarzenia i program obsługi zdarzeń funkcji jest dodawany do wdrożenia kontenera (. Pliku CPP).  
  
 Poniższy przykład deklaruje program obsługi zdarzeń o nazwie `OnClickInCircCtrl`, formantu OK **clickin —** zdarzeń:  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 Ponadto następującego szablonu jest dodawany do `CContainerDlg` Implementacja klasy (. Pliku CPP) dla funkcji Członkowskich procedury obsługi zdarzeń:  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 Aby uzyskać więcej informacji na makra obiekt sink zdarzenia, zobacz [mapy wychwytywania zdarzeń](../mfc/reference/event-sink-maps.md) w *informacje dotyczące biblioteki klas*.  
  
#### <a name="to-create-an-event-handler-function"></a>Aby utworzyć funkcję obsługi zdarzeń  
  
1.  Z widoku klasy wybierz klasę okna dialogowego z formantem ActiveX. Na przykład użyć `CContainerDlg`.  
  
2.  Kliknij w oknie właściwości **zdarzenia** przycisku.  
  
3.  W oknie właściwości wybierz identyfikator formantu osadzonego formantu ActiveX. Na przykład użyć `IDC_CIRCCTRL1`.  
  
     Okno właściwości wyświetla listę zdarzeń, które mogą być uruchamiane przez osadzonego formantu ActiveX. Jakiegokolwiek funkcji członkowskiej pogrubione już ma funkcje obsługi przypisane do niej.  
  
4.  Wybierz zdarzenie ma klasę okna dialogowego obsługi. Na przykład wybierz **kliknij**.  
  
5.  W polu listy rozwijanej po prawej stronie wybierz  **\<Dodaj > ClickCircctrl1**.  
  
6.  Kliknij dwukrotnie ikonę Nowa funkcja obsługi z widoku klasy, aby przejść do kod obsługi zdarzeń w implementacji (. Pliku CPP) `CContainerDlg`.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery kontrolek ActiveX](../mfc/activex-control-containers.md)

