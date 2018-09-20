---
title: Niszczenie Windows ramki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- PostNcDestroy
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 742ea2fedff2e4f044e46242a4152c12855ab15e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396158"
---
# <a name="destroying-frame-windows"></a>Niszczenie okien ramowych

Struktura MFC zarządza zniszczenie okna, a także tworzenie tych oknach skojarzone z framework dokumentów i widoków. Jeśli tworzysz dodatkowe okna, ponosisz odpowiedzialność za zniszczenie ich.

W ramach, gdy użytkownik zamknie okno ramowe domyślny okna [OnClose](../mfc/reference/cwnd-class.md#onclose) obsługi zdarzeń wywołuje [destroywindow —](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatni funkcja elementu członkowskiego, wywoływana, gdy okno Windows zostanie zniszczony [onncdestroy —](../mfc/reference/cwnd-class.md#onncdestroy), który wykonuje niektóre oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) element członkowski funkcji do wykonywania oczyszczania Windows i na koniec wywołania Funkcja wirtualna elementu członkowskiego [postncdestroy —](../mfc/reference/cwnd-class.md#postncdestroy). [CFrameWnd](../mfc/reference/cframewnd-class.md) implementacji `PostNcDestroy` usuwa obiekt okna języka C++. Nigdy nie należy używać języka C++ **Usuń** operatora w oknie ramek. Zamiast nich należy używać słów kluczowych `DestroyWindow`.

Po zamknięciu okna głównego, zamyka aplikację. Jeśli są modyfikowane niezapisane dokumenty, struktura Wyświetla okno komunikatu, aby zadać, czy można zapisywać dokumenty i gwarantuje, że odpowiednie dokumenty są zapisywane w razie potrzeby.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](../mfc/using-frame-windows.md)

