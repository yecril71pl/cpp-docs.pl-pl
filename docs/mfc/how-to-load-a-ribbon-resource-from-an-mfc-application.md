---
title: 'Porady: ładowanie zasobu wstążki z aplikacji MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: 14ba37952d6f8849c51b36901a6bc17404f938e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515157"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Porady: ładowanie zasobu wstążki z aplikacji MFC

Aby użyć zasobu wstążki do aplikacji, należy zmodyfikować ładowanie zasobu Wstążki aplikacji.

### <a name="to-load-a-ribbon-resource"></a>Ładowanie zasobu wstążki

1. Zadeklaruj `Ribbon Control` obiektu `CMainFrame` klasy.

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. W `CMainFrame::OnCreate`, Utwórz i zainicjuj formantu wstążki.

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>Zobacz też

[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)

