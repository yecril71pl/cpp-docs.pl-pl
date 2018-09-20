---
title: Style ramki okna ramowego (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7f0e4bde874fc563535b661108cb68edefd8d977
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46385017"
---
# <a name="frame-window-styles-c"></a>Style okna ramowego (C++)

Okien ramowych, możesz uzyskać za pomocą programu framework są odpowiednie dla większości programów, ale możesz uzyskać większą elastyczność, za pomocą zaawansowanych funkcji [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) i funkcje globalne MFC [afxregisterwndclass — ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` jest funkcją składową z `CWnd`.

Jeśli zastosujesz **WS_HSCROLL** i **WS_VSCROLL** style, które mają ramki głównego okna są natomiast stosowane względem **MDICLIENT** okna, dzięki czemu użytkownicy będą mogli przewijać **MDICLIENT** obszaru.

Jeśli okna **FWS_ADDTOTITLE** (co jest ustawieniem domyślnym) ustawiony bit stylu, widoku nakazuje okno ramowe jakie tytuł wyświetlany na pasku tytułu okna na podstawie nazwy dokumentu tego widoku.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Zarządzanie oknami podrzędnymi MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), okno w obrębie ramki MDI, która zawiera oknami podrzędnymi MDI

- [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [Style okna ramowego](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Zobacz też

[Okna ramowe](../mfc/frame-windows.md)

