---
title: "Formanty MFC ActiveX: Uzyskiwanie dostępu do właściwości otaczających | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b05e6d37a0550cf157dcd43a22689c9db029b51f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających
W tym artykule opisano, jak kontrolki ActiveX można uzyskać dostępu do właściwości otaczających swojego kontenera formantu.  
  
 Formant można uzyskać informacji o jego kontenera podczas uzyskiwania dostępu do właściwości otaczających kontenera. Te właściwości ujawnia cechy wizualne, takie jak kolor tła kontenera bieżącej czcionki używany przez kontener i operacyjne właściwości, takie jak czy kontener jest obecnie w trybie użytkownika lub projektanta. Formant można użyć właściwości otaczających dostosować wygląd i zachowanie w określonym kontenerze, w której jest osadzony. Jednak formant powinien nigdy nie założono, że jego kontenera będzie obsługiwać wszystkie określoną właściwość otoczenia. W rzeczywistości niektóre kontenery mogą nie obsługiwać żadnych właściwości otoczenia w ogóle. W przypadku braku właściwością otoczenia formantu powinien założyć wartość domyślną uzasadnione.  
  
 Aby uzyskać dostęp do właściwości otaczających, wywoływania [COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty). Ta funkcja oczekuje wysłania Identyfikatora dla właściwości otoczenia jako pierwszego parametru (plik OLECTL. H definiuje identyfikatorów wysyłania standardowy zestaw właściwości otaczających).  
  
 Parametry `GetAmbientProperty` funkcji są Identyfikatora wysyłania variant tag wskazujący typ oczekiwany właściwości i wskaźnik do pamięci których wartość ma zostać zwrócony. Typ danych, do którego odwołuje się ten wskaźnik różni się zależnie od typu variant tagu. Funkcja zwraca **TRUE** przypadku kontener obsługuje właściwość, w przeciwnym razie zwraca **FALSE**.  
  
 Poniższy przykładowy kod uzyskuje wartość właściwości otoczenia o nazwie "Przekierowanie". Jeśli ta właściwość nie jest obsługiwana przez kontener, wartością domyślną **TRUE** zakłada, że:  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 Dla wygody `COleControl` dostarcza funkcji pomocnika dostęp do wielu typowych właściwości otoczenia i zwracanie odpowiednie wartości domyślnych właściwości nie są dostępne. Te funkcje pomocnicze są następujące:  
  
-   [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)  
  
-   [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)  
  
-   [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)  
  
    > [!NOTE]
    >  Obiekt wywołujący musi wywołać **wydania ()** zwrócony czcionki.  
  
-   [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)  
  
-   [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)  
  
-   [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)  
  
-   [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)  
  
-   [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)  
  
-   [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)  
  
-   [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)  
  
-   [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)  
  
 W przypadku zmiany wartości właściwości otaczających (za pośrednictwem niektóre akcje kontenera) **OnAmbientPropertyChanged** nosi nazwę funkcji członkowskiej klasy formantu. Przesłonić tę funkcję elementu członkowskiego do obsługi takiego powiadomienia. Parametr **OnAmbientPropertyChanged** jest Identyfikatorem wysyłania odpowiednich właściwości otoczenia. Wartość tego Identyfikatora wysyłania mogą być **DISPID_UNKNOWN**, co oznacza, że co najmniej jednej właściwości otoczenia został zmieniony, ale informacje o tym, które właściwości zostały zainfekowane są niedostępne.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

