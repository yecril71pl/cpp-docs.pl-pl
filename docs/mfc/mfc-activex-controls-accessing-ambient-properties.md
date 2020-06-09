---
title: 'Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: e5c78c9943f8baeadcc1198ee8c96f2023ac0215
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625446"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>Kontrolki ActiveX MFC: uzyskiwanie dostępu do właściwości otaczających

W tym artykule omówiono sposób, w jaki formant ActiveX może uzyskać dostęp do właściwości otoczenia swojego kontenera sterowania.

Kontrolka może uzyskać informacje o jej kontenerze, uzyskując dostęp do właściwości otaczających kontenera. Właściwości te uwidaczniają cechy wizualne, takie jak kolor tła kontenera, bieżącą czcionkę używaną przez kontener i cechy operacyjne, takie jak, czy kontener jest obecnie w trybie użytkownika czy w trybie projektanta. Kontrolka może używać właściwości otoczenia do dostosowywania wyglądu i zachowania do określonego kontenera, w którym jest osadzony. Jednak kontrolka nie powinna zakładać, że jej kontener będzie obsługiwał jakąkolwiek konkretną Właściwość otoczenia. W rzeczywistości niektóre kontenery mogą nie obsługiwać żadnych właściwości otoczenia. W przypadku braku właściwości otoczenia formant powinien przyjąć rozsądną wartość domyślną.

Aby uzyskać dostęp do właściwości otoczenia, należy wywołać metodę [COleControl:: GetAmbientProperty](reference/colecontrol-class.md#getambientproperty). Ta funkcja oczekuje identyfikatora wysyłania dla właściwości otoczenia jako pierwszego parametru (OLECTL pliku. H definiuje identyfikatory wysyłki dla standardowego zestawu właściwości otoczenia.

Parametry `GetAmbientProperty` funkcji to identyfikator wysyłania, tag Variant wskazujący oczekiwany typ właściwości oraz wskaźnik do pamięci, w której ma zostać zwrócona wartość. Typ danych, do których odwołuje się ten wskaźnik, różni się w zależności od tagu Variant. Funkcja zwraca **wartość true** , jeśli kontener obsługuje właściwość, w przeciwnym razie zwraca **wartość false**.

Poniższy przykład kodu pobiera wartość właściwości otoczenia o nazwie "Usermode." Jeśli właściwość nie jest obsługiwana przez kontener, przyjmowana jest domyślna wartość **true** :

[!code-cpp[NVC_MFC_AxUI#30](codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Dla wygody `COleControl` dostarcza funkcje pomocnika, które uzyskują dostęp do wielu najczęściej używanych właściwości otoczenia i zwracają odpowiednie wartości domyślne, gdy właściwości są niedostępne. Te funkcje pomocnika są następujące:

- [COleControl::AmbientBackColor](reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  Obiekt wywołujący musi wywołać `Release( )` zwracaną czcionkę.

- [AmbientForeColor](reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](reference/colecontrol-class.md#ambientshowgrabhandles)

Jeśli wartość właściwości otoczenia ulegnie zmianie (za pomocą pewnej akcji kontenera), `OnAmbientPropertyChanged` wywoływana jest funkcja członkowska kontrolki. Przesłoń tę funkcję elementu członkowskiego, aby obsłużyć takie powiadomienie. Parametr `OnAmbientPropertyChanged` jest identyfikatorem wysyłania zależnej właściwości otaczającej. Wartość tego identyfikatora wysyłania może być DISPID_UNKNOWN, co oznacza, że co najmniej jedna Właściwość otoczenia została zmieniona, ale informacje o tym, które właściwości zostały naruszone, są niedostępne.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
