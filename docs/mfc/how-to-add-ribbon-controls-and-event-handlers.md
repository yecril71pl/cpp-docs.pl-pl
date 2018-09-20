---
title: 'Porady: Dodawanie kontrolek wstążki do programów obsługi zdarzeń | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3c4af695553bc97815915454bda2aae481543e9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427956"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Porady: dodawanie formantów wstążki do programów obsługi zdarzeń

Formanty wstążki są elementy, takie jak przyciski i pola kombi, które dodajesz do paneli. Panele to obszary paska wstążki, wyświetlających grupy pokrewnych formantów.

W tym temacie zostanie otwierania projektanta wstążki, Dodaj przycisk i następnie połączyć zdarzenia, które wyświetla "Hello World".

### <a name="to-open-the-ribbon-designer"></a>Aby otworzyć projektanta wstążki

1. W programie Visual Studio na **widoku** menu, kliknij przycisk **widok zasobów**.

1. W **widok zasobów**, kliknij dwukrotnie zasób wstążki, aby wyświetlić je na powierzchni projektowej.

### <a name="to-add-a-button-and-an-event-handler"></a>Aby dodać przycisk i program obsługi zdarzeń

1. Z **narzędzi**, kliknij przycisk **przycisk** i przeciągnij go do panelu na powierzchni projektowej.

1. Kliknij prawym przyciskiem myszy przycisk, a następnie kliknij przycisk **dodać program obsługi zdarzeń**.

1. W **Kreator obsługi zdarzeń**, Potwierdź ustawienia domyślne i kliknij przycisk **dodawać i edytować**. Aby uzyskać więcej informacji, zobacz [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md).

1. W edytorze kodu Dodaj następujący kod do funkcji obsługi:

```
    MessageBox((LPCTSTR)L"Hello World");

```

## <a name="see-also"></a>Zobacz też

[Przykład RibbonGadgets: Wstążki gadżetów aplikacji](../visual-cpp-samples.md)<br/>
[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

