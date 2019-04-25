---
title: Ogólna sekwencja tworzenia okna
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 949cf72910654b502ca4b57be72bedc2db63c315
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219570"
---
# <a name="general-window-creation-sequence"></a>Ogólna sekwencja tworzenia okna

Podczas tworzenia okna swoich potrzeb, takich jak elementu podrzędnego okna, środowisko wykorzystuje znacznie ten sam proces, którą opisano w [tworzenia dokumentu/widoku](../mfc/document-view-creation.md).

Wszystkich klas okien dostarczonych przez MFC stosują [dwuetapowa konstrukcja](../mfc/one-stage-and-two-stage-construction-of-objects.md). Oznacza to, że podczas wywoływania C++ **nowe** operatora, Konstruktor przydziela i inicjuje obiektu języka C++, ale nie powoduje utworzenia odpowiedniego okna Windows. Zostanie to zrobione później przez wywołanie metody [Utwórz](../mfc/reference/cwnd-class.md#create) funkcji składowej typu obiekt okna.

`Create` Okna Windows sprawia, że funkcja elementu członkowskiego i przechowuje swoje `HWND` w C++ obiektu publicznego elementu członkowskiego danych [m_hWnd](../mfc/reference/cwnd-class.md#m_hwnd). `Create` zapewnia ukończyć elastyczność za pośrednictwem parametrów do utworzenia. Przed wywołaniem `Create`, możesz chcieć rejestrowanie klasy okna za pomocą funkcji globalnych [afxregisterwndclass —](../mfc/reference/application-information-and-management.md#afxregisterwndclass) aby można było ustawić ikonę i klasa style ramki.

Okna ramowe, można użyć [loadframe —](../mfc/reference/cframewnd-class.md#loadframe) funkcja elementu członkowskiego zamiast `Create`. `LoadFrame` sprawia, że okno Windows przy użyciu mniejszej liczby parametrów. Otrzymuje wiele wartości domyślnych od zasobów, w tym podpis ramki, ikony, tabeli akceleratora i menu.

> [!NOTE]
>  Twoje ikonę tabeli akceleratora i zasobów menu musi mieć wspólny identyfikator zasobu, takie jak **IDR_MAINFRAME**, musiały być ładowane przez loadframe —.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Obiekty okna](../mfc/window-objects.md)

- [Rejestrowanie klas"okien"](../mfc/registering-window-classes.md)

- [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie okien](../mfc/creating-windows.md)
