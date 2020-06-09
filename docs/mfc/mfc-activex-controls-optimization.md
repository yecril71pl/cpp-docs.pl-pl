---
title: 'Kontrolki ActiveX MFC: optymalizacja'
ms.date: 09/12/2018
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
ms.openlocfilehash: b4e12889ca1bb5f4bb423a1f1ede1c396f8d60b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615402"
---
# <a name="mfc-activex-controls-optimization"></a>Kontrolki ActiveX MFC: optymalizacja

W tym artykule opisano techniki, których można użyć w celu zoptymalizowania formantów ActiveX w celu uzyskania lepszej wydajności.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

W tych tematach można [wyłączyć opcję Uaktywnij, gdy widoczna](turning-off-the-activate-when-visible-option.md) i [zapewnić interakcję z myszą podczas nieaktywnej](providing-mouse-interaction-while-inactive.md) kontroli dyskusji, która nie tworzy okna do momentu aktywowania. W temacie [zapewniającym bezokienkową aktywację](providing-windowless-activation.md) omówiono kontrolki, które nigdy nie tworzą okna nawet po aktywowaniu.

System Windows ma dwa główne wady obiektów OLE: uniemożliwiają one przezroczyste lub nieprostokątne, gdy aktywne, i dodają duże obciążenie do tworzenia wystąpień i wyświetlania kontrolek. Zwykle tworzenie okna trwa 60% czasu utworzenia kontrolki. Za pomocą jednego udostępnionego okna (zazwyczaj kontenera) i pewnego kodu, formant otrzymuje te same usługi okna, zazwyczaj bez utraty wydajności. Posiadanie okna jest w większości niepotrzebnych nakładów dla obiektu.

Niektóre optymalizacje nie muszą zwiększyć wydajności, gdy kontrolka jest używana w niektórych kontenerach. Na przykład kontenery wydane przed 1996 nie obsługują aktywacji bez okien, więc wdrożenie tej funkcji nie będzie miało zalet w starszych kontenerach. Natomiast niemal każdy kontener obsługuje trwałość, dlatego Optymalizacja kodu trwałości kontrolki prawdopodobnie poprawi swoją wydajność w dowolnym kontenerze. Jeśli formant jest przeznaczony głównie do użycia z jednym określonym typem kontenera, warto zbadać, które z tych optymalizacji są obsługiwane przez ten kontener. Ogólnie rzecz biorąc, należy podjąć próbę wdrożenia jak wiele z tych technik, które mają zastosowanie do danej kontrolki, aby upewnić się, że kontrolka wykonuje, a także może być w szerokim zakresie tablicy kontenerów.

Wiele z tych optymalizacji można zaimplementować za pomocą [Kreatora kontrolek ActiveX MFC](reference/mfc-activex-control-wizard.md)na stronie [Ustawienia kontrolek](reference/control-settings-mfc-activex-control-wizard.md) .

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Opcje optymalizacji OLE w Kreatorze formantów ActiveX MFC

|Ustawienie kontrolki w Kreatorze kontrolek ActiveX MFC|Akcja|Więcej informacji|
|-------------------------------------------------------|------------|----------------------|
|**Aktywuj, gdy** pole wyboru jest widoczne|Clear|[Wyłączanie opcji Aktywuj, gdy widoczna](turning-off-the-activate-when-visible-option.md)|
|Pole wyboru **Aktywacja bez okien**|Wybierz pozycję|[Zapewnianie aktywacji niepowiązanej z oknami](providing-windowless-activation.md)|
|Pole wyboru **odciętego kontekstu urządzenia**|Wybierz pozycję|[Używanie nieobcinanego kontekstu urządzenia](using-an-unclipped-device-context.md)|
|Pole wyboru **Aktywacja bez migotania**|Wybierz pozycję|[Zapewnianie aktywacji pozbawionej migotania](providing-flicker-free-activation.md)|
|**Powiadomienia wskaźnika myszy, gdy pole wyboru nieaktywne**|Wybierz pozycję|[Zapewnianie interakcji z myszą przy braku aktywności](providing-mouse-interaction-while-inactive.md)|
|Pole wyboru **zoptymalizowanego kodu rysowania**|Wybierz pozycję|[Optymalizacja rysowania kontrolek](optimizing-control-drawing.md)|

Aby uzyskać szczegółowe informacje na temat funkcji Członkowskich implementujących te optymalizacje, zobacz [COleControl](reference/colecontrol-class.md).

Aby uzyskać więcej informacji, zobacz:

- [Optymalizacja stanu trwałego i inicjalizacji](optimizing-persistence-and-initialization.md)

- [Zapewnianie aktywacji niepowiązanej z oknami](providing-windowless-activation.md)

- [Wyłączanie opcji Aktywuj, gdy widoczna](turning-off-the-activate-when-visible-option.md)

- [Zapewnianie interakcji z myszą przy braku aktywności](providing-mouse-interaction-while-inactive.md)

- [Zapewnianie aktywacji pozbawionej migotania](providing-flicker-free-activation.md)

- [Używanie nieobcinanego kontekstu urządzenia](using-an-unclipped-device-context.md)

- [Optymalizacja rysowania kontrolek](optimizing-control-drawing.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
