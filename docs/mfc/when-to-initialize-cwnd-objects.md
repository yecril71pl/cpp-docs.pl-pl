---
title: Kiedy inicjować obiekty CWnd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6445190ab3da6ed84dbdd83cd0acab0ba98691f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388436"
---
# <a name="when-to-initialize-cwnd-objects"></a>Kiedy inicjować obiekty CWnd

Nie można utworzyć własne podrzędne systemu windows lub wywołaniem dowolnej funkcji interfejsu Windows API w Konstruktorze typu `CWnd`-pochodnych obiektu. Jest to spowodowane `HWND` dla `CWnd` obiekt nie został jeszcze utworzony. Inicjowanie najbardziej specyficzne dla Windows, takie jak dodanie okien podrzędnych, należy wykonać w [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obsługi wiadomości.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

- [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

