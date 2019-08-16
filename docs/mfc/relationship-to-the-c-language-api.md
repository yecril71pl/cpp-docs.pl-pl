---
title: Relacja z interfejsem API języka C
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 8601dd034dbd73ac035084ad57c51f62e333fd32
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511856"
---
# <a name="relationship-to-the-c-language-api"></a>Relacja z interfejsem API języka C

Pojedyncza cecha, która ustawia bibliotekę Microsoft Foundation Class (MFC), poza innymi bibliotekami klas dla systemu Windows, to bardzo bliskie mapowanie do interfejsu API systemu Windows zapisywanego w języku C. Dodatkowo można na ogół mieszać wywołania biblioteki klas swobodnie za pomocą bezpośrednich wywołań interfejsu API systemu Windows. Ten bezpośredni dostęp nie oznacza jednak, że klasy są kompletną wymianą dla tego interfejsu API. Deweloperzy nadal muszą czasami wykonać bezpośrednie wywołania niektórych funkcji systemu Windows, takich jak [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) i [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), na przykład. Funkcja systemu Windows jest opakowana przez funkcję składową klasy tylko wtedy, gdy istnieje oczywista korzyść.

Ponieważ czasami trzeba wykonać natywne wywołania funkcji systemu Windows, należy mieć dostęp do dokumentacji interfejsu API systemu Windows w języku C. Ta dokumentacja jest dołączona do programu C++Microsoft Visual.

> [!NOTE]
>  Aby zapoznać się z omówieniem działania struktury biblioteki MFC, zobacz [Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Zobacz także

[Ogólne zasady projektowania klas](../mfc/general-class-design-philosophy.md)
