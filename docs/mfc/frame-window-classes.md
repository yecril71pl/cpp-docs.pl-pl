---
title: Klasy okien ramowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2ac60fb8d1b12708c7e64a91beb224ca436e5005
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404530"
---
# <a name="frame-window-classes"></a>Klasy okien ramowych

Każda aplikacja ma jeden "ramką głównego okna," oknem pulpitu, które zazwyczaj ma nazwę aplikacji w jego podpisu. Każdy dokument ma zwykle jedną "okna ramki dokumentu." Okna ramki dokumentu zawiera co najmniej jeden widok, który przedstawia dane dokumentu.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Windows ramek SDI i MDI aplikacji

Dla aplikacji interfejsu SDI istnieje jedno okno ramki pochodzi od klasy [CFrameWnd](../mfc/reference/cframewnd-class.md). To okno jest głównej ramki okna i okna ramki dokumentu. Dla aplikacji MDI ramki głównego okna jest pochodną klasy [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md), i okien ramowych dokumentu, które są podrzędne MDI, pochodzą z klasy [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Korzystanie z klasy okien ramowych lub pochodzić od niego

Te klasy oferują najbardziej funkcje ramki okna, które należy używać w aplikacjach. W normalnych warunkach domyślnego zachowania i wyglądu, jakie zapewniają będzie odpowiadać Twoim potrzebom. Jeśli potrzebujesz dodatkowych funkcji, pochodzi z tych klas.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Klasy okien ramowych tworzone przez Kreatora aplikacji](../mfc/frame-window-classes-created-by-the-application-wizard.md)

- [Style okna ramki](../mfc/frame-window-styles-cpp.md)

- [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Zobacz też

[Okna ramowe](../mfc/frame-windows.md)

