---
title: Niszczenie okien ramowych
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
ms.openlocfilehash: f3b3e022f869a3019f80ba5ee082ce5a959853a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50645409"
---
# <a name="destroying-frame-windows"></a>Niszczenie okien ramowych

Struktura MFC zarządza zniszczenie okna, a także tworzenie tych oknach skojarzone z framework dokumentów i widoków. Jeśli tworzysz dodatkowe okna, ponosisz odpowiedzialność za zniszczenie ich.

W ramach, gdy użytkownik zamknie okno ramowe domyślny okna [OnClose](../mfc/reference/cwnd-class.md#onclose) obsługi zdarzeń wywołuje [destroywindow —](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatni funkcja elementu członkowskiego, wywoływana, gdy okno Windows zostanie zniszczony [onncdestroy —](../mfc/reference/cwnd-class.md#onncdestroy), który wykonuje niektóre oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) element członkowski funkcji do wykonywania oczyszczania Windows i na koniec wywołania Funkcja wirtualna elementu członkowskiego [postncdestroy —](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) implementacji `PostNcDestroy` usuwa obiekt okna języka C++. Nigdy nie należy używać języka C++ **Usuń** operatora w oknie ramek. Zamiast nich należy używać słów kluczowych `DestroyWindow`.

Po zamknięciu okna głównego, zamyka aplikację. Jeśli są modyfikowane niezapisane dokumenty, struktura Wyświetla okno komunikatu, aby zadać, czy można zapisywać dokumenty i gwarantuje, że odpowiednie dokumenty są zapisywane w razie potrzeby.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

