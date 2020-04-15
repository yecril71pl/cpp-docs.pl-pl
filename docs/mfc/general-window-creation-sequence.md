---
title: Ogólna sekwencja tworzenia okna
ms.date: 11/04/2016
helpviewer_keywords:
- sequence [MFC], window creation
- frame windows [MFC], creating
- windows [MFC], creating
- sequence [MFC]
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
ms.openlocfilehash: fb10ced78e230316a6e2982f24c1fb6e2e52ed8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364269"
---
# <a name="general-window-creation-sequence"></a>Ogólna sekwencja tworzenia okna

Podczas tworzenia własnego okna, takiego jak okno podrzędne, struktura używa tego samego procesu, który opisano w [dokumencie/utworzeniu widoku.](../mfc/document-view-creation.md)

Wszystkie klasy okien dostarczone przez MFC zatrudniają [konstrukcję dwuetapową.](../mfc/one-stage-and-two-stage-construction-of-objects.md) Oznacza to, że podczas wywołania **nowego** operatora języka C++ konstruktor przydziela i inicjuje obiekt C++, ale nie tworzy odpowiedniego okna systemu Windows. Odbywa się to później, wywołując [Funkcję Create](../mfc/reference/cwnd-class.md#create) element członkowski obiektu okna.

Funkcja `Create` elementu członkowskiego tworzy okno `HWND` systemu Windows i przechowuje go w publicznej m_hWnd elementu członkowskiego danych obiektu C++ [.](../mfc/reference/cwnd-class.md#m_hwnd) `Create`zapewnia pełną elastyczność w zakresie parametrów tworzenia. Przed `Create`wywołaniem można zarejestrować klasę okna z globalną funkcją [AfxRegisterWndClass](../mfc/reference/application-information-and-management.md#afxregisterwndclass) w celu ustawienia stylów ikony i klasy dla ramki.

W przypadku okien ramek można użyć funkcji `Create`elementu członkowskiego [LoadFrame](../mfc/reference/cframewnd-class.md#loadframe) zamiast . `LoadFrame`sprawia, że okno systemu Windows przy użyciu mniejszej liczby parametrów. Pobiera wiele wartości domyślnych z zasobów, w tym podpis ramki, ikona, tabela akceleratora i menu.

> [!NOTE]
> Ikona, tabela akceleratora i zasoby menu muszą mieć wspólny identyfikator zasobu, taki jak **IDR_MAINFRAME**, aby można je było załadować przez loadframe.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Obiekty okienne](../mfc/window-objects.md)

- [Rejestrowanie okna "klasy"](../mfc/registering-window-classes.md)

- [Niszczenie obiektów okiennych](../mfc/destroying-window-objects.md)

- [Tworzenie okien ramek dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Tworzenie okien](../mfc/creating-windows.md)
