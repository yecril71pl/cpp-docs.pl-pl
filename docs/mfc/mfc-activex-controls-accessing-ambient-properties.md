---
title: 'Kontrolki ActiveX MFC: Uzyskiwanie dostępu do właściwości otaczających | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aaa379513695f3cd39589a1009e3a157d957761
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407914"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających

W tym artykule omówiono, jak kontrolki ActiveX mogą dostęp do właściwości otaczających swojego kontenera kontrolki.

Kontrolki można uzyskać informacje o jego kontener, uzyskując dostęp do właściwości otaczających kontenera. Te właściwości uwidocznić visual cechami, takimi jak kolor tła kontenera bieżącej czcionki używany przez kontener i charakterystyk operacyjnych, takich jak tego, czy kontener jest obecnie w trybie użytkownika lub projektanta. Kontrolki można użyć właściwości otoczenia, można dostosować wygląd i zachowanie do określonego kontenera, w której jest osadzony. Jednak kontrolki powinien nigdy nie zakładaj, czy jego kontenera będzie obsługiwać dowolną określoną właściwość otoczenia. W rzeczywistości niektóre kontenery mogą nie obsługiwać dowolne właściwości otoczenia wcale. W przypadku braku zmieniono właściwość kontrolki powinien założyć na rozsądną wartość domyślną.

Aby uzyskać dostęp do właściwości otoczenia, wywoływania [COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty). Ta funkcja oczekuje Identyfikatora wysyłania dla właściwości otoczenia jako pierwszy parametr (plik OLECTL. H definiuje identyfikatorów wysyłania standardowy zestaw właściwości otoczenia).

Parametry `GetAmbientProperty` funkcję są Identyfikatora wysyłania wariantu znacznika wskazujący oczekiwanym typem właściwości i wskaźnik do pamięci, gdzie powinna zostać zwrócona wartość. Typ danych, do którego odwołuje się ten wskaźnik różnią się w zależności od typu variant tagu. Funkcja zwraca **TRUE** Jeśli kontener obsługuje właściwości, w przeciwnym razie zwraca **FALSE**.

Poniższy przykładowy kod uzyskuje wartość właściwości otoczenia, o nazwie "Przekierowywania." Jeśli właściwość nie jest obsługiwana przez kontener wartość domyślną **TRUE** zakłada, że:

[!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Dla Twojej wygody `COleControl` dostarcza funkcje pomocnicze, dostęp do wielu powszechnie używanych właściwości otoczenia, które zwracają odpowiednie wartości domyślne, jeśli właściwości nie są dostępne. Te funkcje pomocnicze są następujące:

- [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  Obiekt wywołujący musi wywołać `Release( )` na zwracany czcionki.

- [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)

Jeśli wartość właściwości otoczenia zmieni się (za pośrednictwem niektóre działania kontenera) `OnAmbientPropertyChanged` nosi nazwę funkcji składowej typu kontrolki. Zastąpienie tej funkcji elementu członkowskiego, aby obsłużyć takie powiadomienie. Parametr `OnAmbientPropertyChanged` jest Identyfikatorem wysyłania dotyczy właściwości otoczenia. Wartość tego Identyfikatora wysyłania mogą być DISPID_UNKNOWN, co oznacza, że co najmniej jednej właściwości otoczenia został zmieniony, ale informacje na temat tego, jakie właściwości są niedostępne.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

