---
title: 'Instrukcje: Dodawanie formantów wstążki do programów obsługi zdarzeń'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: c21e8b86962ebf37ca1a06bae056d09b9a9dbb2f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770126"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Instrukcje: Dodawanie formantów wstążki do programów obsługi zdarzeń

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

## <a name="see-also"></a>Zobacz także

[Przykład RibbonGadgets: Aplikacji gadżetów wstążki](../overview/visual-cpp-samples.md)<br/>
[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)
