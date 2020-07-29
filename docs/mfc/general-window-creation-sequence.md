---
title: Ogólna sekwencja tworzenia okna
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: 63b5e0131642692d9372c148827a583f19114fb9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223164"
---
# <a name="general-window-creation-sequence"></a>Ogólna sekwencja tworzenia okna

W przypadku tworzenia własnego okna, takiego jak okno podrzędne, struktura używa znacznie tego samego procesu, który został opisany w temacie [Tworzenie dokumentu/widoku](document-view-creation.md).

Wszystkie klasy okna udostępniane przez MFC wykorzystują [konstrukcję dwuetapową](one-stage-and-two-stage-construction-of-objects.md). Oznacza to, że podczas wywołania **`new`** operatora c++ Konstruktor przydziela i inicjuje obiekt C++, ale nie tworzy odpowiedniego okna systemu Windows. Jest to wykonywane później przez wywołanie funkcji [tworzenia](reference/cwnd-class.md#create) elementu członkowskiego obiektu okna.

`Create`Funkcja członkowska powoduje, że okno systemu Windows i przechowuje jego `HWND` w [m_hWnd](reference/cwnd-class.md#m_hwnd)publicznej składowej danych obiektu C++. `Create`zapewnia pełną elastyczność nad parametrami tworzenia. Przed wywołaniem `Create` można zarejestrować klasę okna przy użyciu funkcji globalnej [AfxRegisterWndClass —](reference/application-information-and-management.md#afxregisterwndclass) w celu ustawienia stylu ikon i klas dla ramki.

W przypadku okien ramowych można użyć funkcji składowej [LoadFrame](reference/cframewnd-class.md#loadframe) zamiast `Create` . `LoadFrame`sprawia, że okno systemu Windows korzysta z mniejszej liczby parametrów. Pobiera on wiele wartości domyślnych z zasobów, w tym podpis ramki, ikonę, tabelę akceleratora i menu.

> [!NOTE]
> Twoje ikony, tabele akceleratorów i zasoby menu muszą mieć wspólny identyfikator zasobu, taki jak **IDR_MAINFRAME**, do załadowania przez LoadFrame.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Obiekty okna](window-objects.md)

- [Rejestrowanie okna "classes"](registering-window-classes.md)

- [niszczenie obiektów okien](destroying-window-objects.md)

- [Tworzenie okien ramowych dokumentu](creating-document-frame-windows.md)

## <a name="see-also"></a>Zobacz także

[Tworzenie okien](creating-windows.md)
