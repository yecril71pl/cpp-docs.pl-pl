---
title: Kontenery kontrolek ActiveX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ActiveX control containers [MFC]
- OLE controls [MFC], containers
ms.assetid: 0eb1a713-e607-4c79-a0c7-67c5f1fd5fab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7d8a6498edf33bbf51fa9ab0de04d5d58ebd11a
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45534849"
---
# <a name="activex-control-containers"></a>Kontenery kontrolek ActiveX
Kontener formantu ActiveX jest kontenerem, który w pełni obsługuje formanty ActiveX i zastosować je do swoich własnych systemu windows lub w oknach dialogowych. Kontrolki ActiveX jest element oprogramowania wielokrotnego użytku, który można użyć w wielu projektach deweloperskich. Formanty umożliwiają użytkownikowi aplikacji bazy danych programu access, monitorować dane i różne opcje w aplikacjach. Aby uzyskać więcej informacji na temat formantów ActiveX, zobacz artykuł [kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md).  

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji, zobacz [formantów ActiveX](activex-controls.md).
  
 Kontenery kontrolek zwykle wykonać dwa formularze w projekcie:  
  
-   Okna dialogowe i systemu windows okno dialogowe przypominające takich jak widoki formularzy, gdzie formantu ActiveX jest używany gdzieś w oknie dialogowym.  
  
-   Windows w aplikacji, gdy formant ActiveX jest używana w pasku narzędzi lub innej lokalizacji, w oknie użytkownika.  
  
 Udostępniane ActiveX kontener formantu interakcję z kontrolką za pośrednictwem [metody](../mfc/mfc-activex-controls-methods.md) i [właściwości](../mfc/mfc-activex-controls-properties.md). Te metody i właściwości, które mogą być dostępne i zmodyfikowane przez kontener formantu, są dostępne za pośrednictwem klasy otoki w projekcie kontener formantu ActiveX. Osadzony formant ActiveX mogą również wchodzić w interakcje z kontenerem przez wyzwalanie (wysyłającym) [zdarzenia](../mfc/mfc-activex-controls-events.md) do kontenera, w którym wystąpiło akcji powiadamiania. Kontener formantu mogą być wykonywane działania tych powiadomień lub nie.  
  
 Dodatkowe artykuły omówiono kilku tematach, od tworzenia projektu kontener formantu ActiveX na podstawową implementację problemy związane z kontenerami formantu ActiveX utworzona za pomocą języka Visual C++:  
  
-   [Tworzenie kontenera kontrolek ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control-container.md)  
  
-   [Kontenery dla kontrolek ActiveX](../mfc/containers-for-activex-controls.md)  
  
-   [Kontenery kontrolek ActiveX: ręczne włączanie zawierania kontrolek ActiveX](../mfc/activex-control-containers-manually-enabling-activex-control-containment.md)  
  
-   [Kontenery kontrolek ActiveX: wstawianie kontrolki do aplikacji kontenera kontrolek](../mfc/inserting-a-control-into-a-control-container-application.md)  
  
-   [Kontenery kontrolek ActiveX: łączenie kontrolki ActiveX ze zmienną składową](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md)  
  
-   [Kontenery kontrolek ActiveX: Obsługa zdarzeń z ActiveX sterowania](../mfc/activex-control-containers-handling-events-from-an-activex-control.md)  
  
-   [Kontenery kontrolek ActiveX: wyświetlanie i modyfikowanie właściwości kontrolki](../mfc/activex-control-containers-viewing-and-modifying-control-properties.md)  
  
-   [Kontenery kontrolek ActiveX: programowanie kontrolek ActiveX w kontenerze kontrolek ActiveX](../mfc/programming-activex-controls-in-a-activex-control-container.md)  
  
-   [Kontenery kontrolek ActiveX: używanie kontrolek w kontenerze innym niż okno dialogowe](../mfc/activex-control-containers-using-controls-in-a-non-dialog-container.md)  
  
 Aby uzyskać więcej informacji o używaniu kontrolki ActiveX w oknie dialogowym, zobacz [Edytor okien dialogowych](../windows/dialog-editor.md) tematów.  
  
 Aby uzyskać listę artykułów wyjaśniających szczegółów związanych z tworzeniem kontrolek ActiveX przy użyciu języka Visual C++ i klasy kontrolek MFC ActiveX, zobacz [kontrolki MFC ActiveX](../mfc/mfc-activex-controls.md). Artykuły są pogrupowane według kategorii funkcjonalności.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

