---
title: 'Instrukcje: Ładowanie zasobu wstążki z aplikacji MFC'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160331"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>Instrukcje: Ładowanie zasobu wstążki z aplikacji MFC

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

## <a name="see-also"></a>Zobacz także

[Projektant wstążki (MFC)](../mfc/ribbon-designer-mfc.md)
