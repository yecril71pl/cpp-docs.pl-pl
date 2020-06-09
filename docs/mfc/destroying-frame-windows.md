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
ms.openlocfilehash: 4bc7945ecd9aee9021ce97fa3ea05f512c58fe20
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621919"
---
# <a name="destroying-frame-windows"></a>Niszczenie okien ramowych

Struktura MFC zarządza zniszczeniem okna oraz tworzeniem tych okien skojarzonych z dokumentami i widokami struktury. W przypadku tworzenia dodatkowych okien użytkownik jest odpowiedzialny za ich zniszczenie.

W strukturze, gdy użytkownik zamknie okno ramki, domyślna procedura obsługi [OnClose](reference/cwnd-class.md#onclose) okna wywołuje [DestroyWindow](reference/cwnd-class.md#destroywindow). Ostatnia funkcja członkowska wywoływana, gdy okno systemu Windows jest niszczone to [OnNcDestroy](reference/cwnd-class.md#onncdestroy), która wykonuje pewne oczyszczanie, wywołuje [domyślną](reference/cwnd-class.md#default) funkcję członkowską w celu przeprowadzenia oczyszczania systemu Windows i po raz ostatni wywołuje wirtualną funkcję członkowską [PostNcDestroy](reference/cwnd-class.md#postncdestroy). Implementacja [obiektu CFrameWnd](reference/cframewnd-class.md) `PostNcDestroy` usuwania obiektu okna języka C++. Nigdy nie należy używać operatora **delete** języka C++ w oknie ramki. Zamiast tego użyj polecenia cmdlet `DestroyWindow`.

Gdy okno główne zostanie zamknięte, aplikacja zostanie zamknięta. W przypadku zmodyfikowania niezapisanych dokumentów w strukturze zostanie wyświetlone okno komunikatu z monitem o zapisanie dokumentów i zagwarantowanie, że odpowiednie dokumenty zostały zapisane w razie potrzeby.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Tworzenie okien ramowych dokumentu](creating-document-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Używanie okien ramowych](using-frame-windows.md)
