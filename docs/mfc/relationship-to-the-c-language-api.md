---
title: Relacja z interfejsem API języka C
ms.date: 11/04/2016
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
ms.openlocfilehash: 1fbd4d332f5ade1cb9415448b138ac5bc838307d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372824"
---
# <a name="relationship-to-the-c-language-api"></a>Relacja z interfejsem API języka C

Pojedynczą cechą, która odróżnia bibliotekę microsoft foundation class (MFC) od innych bibliotek klas dla systemu Windows, jest bardzo zbliżone mapowanie do interfejsu API systemu Windows napisanego w języku C. Ponadto można ogólnie mieszać wywołania do biblioteki klas swobodnie z bezpośrednich wywołań do interfejsu API systemu Windows. Ten bezpośredni dostęp nie oznacza jednak, że klasy są kompletnym zamiennikiem tego interfejsu API. Deweloperzy muszą nadal od czasu do czasu wykonywać bezpośrednie wywołania niektórych funkcji systemu Windows, takich jak [SetCursor](/windows/win32/api/winuser/nf-winuser-setcursor) i [GetSystemMetrics](/windows/win32/api/winuser/nf-winuser-getsystemmetrics), na przykład. Funkcja systemu Windows jest zawijana przez funkcję elementu członkowskiego klasy tylko wtedy, gdy istnieje wyraźna zaleta, aby to zrobić.

Ponieważ czasami trzeba wywołać natywną funkcję systemu Windows, należy mieć dostęp do dokumentacji interfejsu API systemu Windows w języku C. Ta dokumentacja jest dołączona do programu Microsoft Visual C++.

> [!NOTE]
> Aby zapoznać się z omówieniem działania struktury biblioteki MFC, zobacz [Używanie klas do pisania aplikacji dla systemu Windows](../mfc/using-the-classes-to-write-applications-for-windows.md).

## <a name="see-also"></a>Zobacz też

[Ogólne zasady projektowania klas](../mfc/general-class-design-philosophy.md)
