---
title: Kiedy inicjować obiekty CWnd
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: aa396ade2e8ab4e1245e161423de7bd5bfafaaf8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405719"
---
# <a name="when-to-initialize-cwnd-objects"></a>Kiedy inicjować obiekty CWnd

Nie można utworzyć własne podrzędne systemu windows lub wywołaniem dowolnej funkcji interfejsu Windows API w Konstruktorze typu `CWnd`-pochodnych obiektu. Jest to spowodowane `HWND` dla `CWnd` obiekt nie został jeszcze utworzony. Inicjowanie najbardziej specyficzne dla Windows, takie jak dodanie okien podrzędnych, należy wykonać w [OnCreate](../mfc/reference/cwnd-class.md#oncreate) obsługi wiadomości.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

- [Tworzenie dokumentu/widoku](../mfc/document-view-creation.md)

## <a name="see-also"></a>Zobacz także

[Używanie okien ramowych](../mfc/using-frame-windows.md)
