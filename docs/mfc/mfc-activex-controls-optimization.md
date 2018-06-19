---
title: 'Formanty MFC ActiveX: Optymalizacja | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: c91f147637b53250f8d373af9950d6205c82d3e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355314"
---
# <a name="mfc-activex-controls-optimization"></a>Kontrolki ActiveX MFC: optymalizacja
W tym artykule opisano metod, które służy do optymalizacji formantów ActiveX w celu poprawy wydajności.  
  
 Tematy [Włączanie poza aktywować gdy widoczny jest opcja](../mfc/turning-off-the-activate-when-visible-option.md) i [dostarczanie myszy interakcji podczas nieaktywne](../mfc/providing-mouse-interaction-while-inactive.md) omówienia kontrolki, których nie należy tworzyć okna do momentu aktywowania. Temat [zapewnianie aktywacji niepowiązanej z oknami](../mfc/providing-windowless-activation.md) omówiono formantów, które nigdy nie twórz okna, nawet wtedy, gdy są one aktywowane.  
  
 W systemie Windows ma dwa główne wady dla obiektów OLE: obiekty zapobiegają przezroczysty lub nieprostokątny, gdy jest aktywny i dodać duże obciążenie podczas tworzenia wystąpienia i wyświetlania formantów. Trwa tworzenie okna zazwyczaj, 60 procent czasu utworzenia formantu. Z poziomu jednego okna udostępnionych (zazwyczaj kontenera) i wysyłania kodu formantu odbiera te same usługi okna, zazwyczaj bez utraty wydajności. Okno jest przede wszystkim niepotrzebnego obciążenia dla obiekt.  
  
 Niektóre funkcje optymalizacji nie zawsze poprawia wydajności, gdy formant jest używany w określonych kontenerach. Na przykład kontenery wydane przed 1996 nie obsługuje aktywacji niepowiązanej z oknami, dlatego wdrażanie tej funkcji nie zapewniają korzyści w kontenerach starszych. Niemal każdego kontenera obsługuje jednak trwałości, więc Optymalizacja kodu trwałości formantu prawdopodobnie zwiększenia wydajności w dowolnym kontenerze. Jeśli formant jest przeznaczony specjalnie do użycia z jednego określonego typu kontenera, warto badania która z tych optymalizacji jest obsługiwana przez tego kontenera. Ogólnie rzecz biorąc jednak należy zaimplementować jak wiele z tych metod, ponieważ mają zastosowanie do określonego formantu do upewnij się, że formant wykonuje oraz jego prawdopodobnie w szerokiej gamy kontenerów.  
  
 Można zaimplementować wiele z tych optymalizacji za pośrednictwem [Kreator kontrolek ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)na [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) strony.  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Opcje optymalizacji OLE Kreator kontrolek ActiveX MFC  
  
|Ustawienia formantu w Kreator kontrolek ActiveX MFC|Akcja|Więcej informacji|  
|-------------------------------------------------------|------------|----------------------|  
|**Uaktywnij, gdy widoczny** pole wyboru|Wyczyść|[Wyłączanie aktywacji, gdy opcja widoczne](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**Aktywacja bez okien** pole wyboru|Wybierz|[Zapewnianie aktywacji niepowiązanej z oknami](../mfc/providing-windowless-activation.md)|  
|**Nieobcinanego kontekstu urządzenia** pole wyboru|Wybierz|[Używanie nieobcinanego kontekstu urządzenia](../mfc/using-an-unclipped-device-context.md)|  
|**Pozbawione migotania aktywacji** pole wyboru|Wybierz|[Zapewnianie aktywacji pozbawionej migotania](../mfc/providing-flicker-free-activation.md)|  
|**Mysz powiadomienia wskaźnika, gdy nieaktywny** pole wyboru|Wybierz|[Zapewnianie interakcji z myszą przy braku aktywności](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**Zoptymalizowany kod rysowania** pole wyboru|Wybierz|[Optymalizacja rysowania kontrolek](../mfc/optimizing-control-drawing.md)|  
  
 Aby uzyskać szczegółowe informacje dotyczące funkcji elementów członkowskich, które implementują te optymalizacje, zobacz [colecontrol —](../mfc/reference/colecontrol-class.md). Funkcje Członkowskie są wyświetlane według użycia, takich jak [operacji bez okien](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) i [nieaktywne wskaźnika funkcji obsługi](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df).  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Optymalizacja stanu trwałego i inicjalizacji](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [Zapewnianie aktywacji niepowiązanej z oknami](../mfc/providing-windowless-activation.md)  
  
-   [Wyłączanie aktywacji, gdy opcja widoczne](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [Zapewnianie interakcji z myszą przy braku aktywności](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [Zapewnianie aktywacji pozbawionej migotania](../mfc/providing-flicker-free-activation.md)  
  
-   [Używanie nieobcinanego kontekstu urządzenia](../mfc/using-an-unclipped-device-context.md)  
  
-   [Optymalizacja rysowania kontrolek](../mfc/optimizing-control-drawing.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

