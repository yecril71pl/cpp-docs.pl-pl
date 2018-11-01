---
title: Klasy okien ramowych (Windows)
ms.date: 11/04/2016
f1_keywords:
- vc.classes.frame
helpviewer_keywords:
- frame window classes [MFC], reference
ms.assetid: 6342ec5f-f922-4da8-a78e-2f5f994c7142
ms.openlocfilehash: 93df9ce745fc907425f1a840ffb7d16a696831fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50514341"
---
# <a name="frame-window-classes-windows"></a>Klasy okien ramowych (Windows)

Okna ramowe są okna, aplikacji lub jej część aplikacji. Okna ramowe zawierają zwykle innych okien, takie jak widoki, paski narzędzi i pasków stanu. W przypadku właściwości `CMDIFrameWnd`, mogą one zawierać `CMDIChildWnd` pośrednio obiektów.

[CFrameWnd](../mfc/reference/cframewnd-class.md)<br/>
Klasa bazowa dla aplikacji interfejsu SDI ramki głównego okna. Również klasę bazową dla wszystkich innych klas okna ramki.

[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)<br/>
Klasa bazowa dla okna głównej ramki aplikacji MDI.

[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)<br/>
Klasa bazowa dla okien ramowych dokumentu w aplikacji MDI.

[CMiniFrameWnd](../mfc/reference/cminiframewnd-class.md)<br/>
Okno ramki w połowie wysokości zwykle widoczne wokół przestawnych pasków narzędzi.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Udostępnia okno ramowe w celu wyświetlenia, gdy dokument serwera jest edytowany w miejscu.

## <a name="related-class"></a>Klasy pokrewne

Klasa `CMenu` udostępnia interfejs, przez które ma dostęp do menu swojej aplikacji. Jest to przydatne do manipulowania menu dynamicznie w czasie wykonywania. na przykład podczas dodawania lub usuwania elementów menu, zgodnie z kontekstu. Mimo że menu są najczęściej używane z okien ramowych, ich można również za pomocą okien dialogowych i innych oknach nonchild.

[CMenu](../mfc/reference/cmenu-class.md)<br/>
Hermetyzuje `HMENU` dojścia do paska menu i wyskakujących menu aplikacji.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

