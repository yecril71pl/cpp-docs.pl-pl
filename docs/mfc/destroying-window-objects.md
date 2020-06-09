---
title: Likwidowanie obiektów okien
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 22b483c1005931b229453ae229935c0e716ab726
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621861"
---
# <a name="destroying-window-objects"></a>Likwidowanie obiektów okien

Należy zachować ostrożność przy użyciu własnych okien podrzędnych, aby zniszczyć obiekt okna języka C++, gdy użytkownik zakończy pracę z oknem. Jeśli te obiekty nie zostaną zniszczone, aplikacja nie odzyska swojej pamięci. Na szczęście środowisko zarządza zniszczeniem okna oraz tworzeniem okien ramowych, widoków i okien dialogowych. W przypadku tworzenia dodatkowych okien użytkownik jest odpowiedzialny za ich zniszczenie.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Sekwencja niszczenia okna](window-destruction-sequence.md)

- [Przydzielanie i cofanie alokacji pamięci okna](allocating-and-deallocating-window-memory.md)

- [Odłączanie elementu CWnd od jego elementu HWND](detaching-a-cwnd-from-its-hwnd.md)

- [Ogólna sekwencja tworzenia okna](general-window-creation-sequence.md)

- [Niszczenie okien ramowych](destroying-frame-windows.md)

## <a name="see-also"></a>Zobacz też

[Obiekty okien](window-objects.md)
