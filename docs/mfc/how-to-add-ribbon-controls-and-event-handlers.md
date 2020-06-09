---
title: 'Porady: dodawanie formantów wstążki do programów obsługi zdarzeń'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: 560524c36dbf57faec3b4b6372cade047f9fe7de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618483"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Porady: dodawanie formantów wstążki do programów obsługi zdarzeń

Kontrolki wstążki to elementy, takie jak przyciski i pola kombi, które można dodać do paneli. Panele są obszarami paska wstążki, który wyświetla grupę powiązanych kontrolek.

W tym temacie należy otworzyć projektanta wstążki, dodać przycisk, a następnie połączyć zdarzenie, które wyświetla "Hello world".

### <a name="to-open-the-ribbon-designer"></a>Aby otworzyć projektanta wstążki

1. W programie Visual Studio, w menu **Widok** kliknij **Widok zasobów**.

1. W **Widok zasobów**kliknij dwukrotnie zasób wstążki, aby wyświetlić go na powierzchni projektowej.

### <a name="to-add-a-button-and-an-event-handler"></a>Aby dodać przycisk i procedurę obsługi zdarzeń

1. Na **pasku narzędzi**kliknij **przycisk** i przeciągnij go do panelu na powierzchni projektowej.

1. Kliknij prawym przyciskiem myszy przycisk, a następnie kliknij pozycję **Dodaj program obsługi zdarzeń**.

1. W **Kreatorze obsługi zdarzeń**Potwierdź ustawienia domyślne, a następnie kliknij przycisk **Dodaj i edytuj**. Aby uzyskać więcej informacji, zobacz [Kreator obsługi zdarzeń](../ide/event-handler-wizard.md).

1. W edytorze kodu Dodaj następujący kod do funkcji obsługi:

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>Zobacz też

[Przykład RibbonGadgets: aplikacja gadżetów wstążki](../overview/visual-cpp-samples.md)<br/>
[Projektant wstążki (MFC)](ribbon-designer-mfc.md)
