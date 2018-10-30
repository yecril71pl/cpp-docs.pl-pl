---
title: 'Kontrolki ActiveX MFC: Optymalizacja | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a583b0b70473698963841a3bd9c84c79472eb529
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204447"
---
# <a name="mfc-activex-controls-optimization"></a>Kontrolki ActiveX MFC: optymalizacja

W tym artykule opisano techniki, które można użyć, aby zoptymalizować swoje kontrolek ActiveX w celu zapewnienia lepszej wydajności.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

Tematy [włączenie wyłączanie opcji aktywacji w przypadku widoczne](../mfc/turning-off-the-activate-when-visible-option.md) i [dostarczanie myszy interakcji podczas nieaktywne](../mfc/providing-mouse-interaction-while-inactive.md) omówienia formantów, które nie należy tworzyć okna do momentu aktywowania. Temat [zapewnianie aktywacji niepowiązanej z oknami](../mfc/providing-windowless-activation.md) w tym artykule omówiono formantów, które nigdy nie twórz oknie, nawet wtedy, gdy są one aktywowane.

Windows ma dwie główne wady dla obiektów OLE: one uniemożliwić obiekty obszarów przezroczystych lub nieprostokątne, gdy jest ona aktywna i dodać duże obciążenie podczas tworzenia wystąpienia i wyświetlania kontrolki. Trwa tworzenie okna zazwyczaj, 60% w czasie tworzenia kontrolki. Za pomocą jednego okna udostępnionego (zazwyczaj kontenera) i wysyłający kodu kontrolki odbiera tych samych usług okna zazwyczaj bez utraty wydajności. Okno to przede wszystkim niepotrzebne koszty dla obiektu.

Niektóre optymalizacje nie zawsze poprawić wydajność, gdy formant jest używany w określonych kontenerach. Na przykład kontenery wydanego przed 1996 roku nie obsługiwał aktywacji niepowiązanej z oknami, więc wdrażanie tej funkcji, nie będą umożliwiać korzyści w kontenerach starsze. Jednak prawie w każdym kontenerze obsługuje trwałość, dzięki czemu Optymalizacja kodu trwałości kontroli nad prawdopodobnie zwiększenia wydajności w dowolnym kontenerze. Jeśli formant jest przeznaczony specjalnie do użycia z jednego określonego typu kontenera, warto zbadać które z tych optymalizacjach jest obsługiwana przez tego kontenera. Ogólnie rzecz biorąc należy jednak zaimplementować wiele z tych metod, ponieważ mają zastosowanie do określonego formantu do upewnij się, że formant wykonuje oraz jego prawdopodobnie mogą w szerokiej gamy kontenerów.

Możesz zaimplementować wiele z tych optymalizacji za pośrednictwem [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)na [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony.

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Opcje optymalizacji OLE Kreator kontrolek ActiveX MFC

|Ustawienia formantu w Kreator kontrolek ActiveX MFC|Akcja|Więcej informacji|
|-------------------------------------------------------|------------|----------------------|
|**Uaktywnij, gdy jest to widoczne** pola wyboru|Usuń zaznaczenie|[Wyłączanie aktywacji, gdy opcji widoczności](../mfc/turning-off-the-activate-when-visible-option.md)|
|**Aktywacji niepowiązanej z oknami** pola wyboru|Wybierz|[Zapewnianie aktywacji niepowiązanej z oknami](../mfc/providing-windowless-activation.md)|
|**Nieobcinanego kontekstu urządzenia** pola wyboru|Wybierz|[Używanie nieobcinanego kontekstu urządzenia](../mfc/using-an-unclipped-device-context.md)|
|**Migotania aktywacji** pola wyboru|Wybierz|[Zapewnianie aktywacji pozbawionej migotania](../mfc/providing-flicker-free-activation.md)|
|**Powiadomienia wskaźnika, gdy nieaktywna myszy** pola wyboru|Wybierz|[Zapewnianie interakcji z myszą przy braku aktywności](../mfc/providing-mouse-interaction-while-inactive.md)|
|**Zoptymalizowane pod kątem kodu rysowania** pola wyboru|Wybierz|[Optymalizacja rysowania kontrolek](../mfc/optimizing-control-drawing.md)|

Aby uzyskać szczegółowe informacje dotyczące funkcji elementów członkowskich, które implementują te optymalizacje, zobacz [COleControl](../mfc/reference/colecontrol-class.md).

Aby uzyskać więcej informacji, zobacz:

- [Optymalizacja stanu trwałego i inicjalizacji](../mfc/optimizing-persistence-and-initialization.md)

- [Zapewnianie aktywacji niepowiązanej z oknami](../mfc/providing-windowless-activation.md)

- [Wyłączanie aktywacji, gdy opcji widoczności](../mfc/turning-off-the-activate-when-visible-option.md)

- [Zapewnianie interakcji z myszą przy braku aktywności](../mfc/providing-mouse-interaction-while-inactive.md)

- [Zapewnianie aktywacji pozbawionej migotania](../mfc/providing-flicker-free-activation.md)

- [Używanie nieobcinanego kontekstu urządzenia](../mfc/using-an-unclipped-device-context.md)

- [Optymalizacja rysowania kontrolek](../mfc/optimizing-control-drawing.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

