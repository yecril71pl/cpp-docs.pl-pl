---
title: Schowek
ms.date: 11/04/2016
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
ms.openlocfilehash: d405a7bbe15d2658380e19c1c908e57f2e40a574
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508932"
---
# <a name="clipboard"></a>Schowek

W tej rodzinie artykułów wyjaśniono, jak zaimplementować obsługę Schowka systemu Windows w aplikacjach MFC. Schowek systemu Windows jest używany na dwa sposoby:

- Implementowanie standardowych poleceń menu edycji, takich jak wycinanie, kopiowanie i wklejanie.

- Implementowanie jednolitego transferu danych za pomocą przeciągania i upuszczania (OLE).

Schowek jest standardową metodą transferu danych między źródłem a miejscem docelowym. Może być również bardzo przydatne w operacjach OLE. W przypadku pojawieniu OLE istnieją dwa mechanizmy w systemie Windows. Standardowy interfejs API Schowka systemu Windows jest nadal dostępny, ale został uzupełniony mechanizmem transferu danych OLE. Funkcja OLE Uniform Data Transfer (UDT) obsługuje wycinanie, kopiowanie i wklejanie ze schowka i przeciąganie i upuszczanie.

Schowek jest usługą systemową udostępnioną przez całą sesję systemu Windows, więc nie ma własnego dojścia ani klasy. Schowek można zarządzać za pomocą funkcji członkowskich klasy [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Kiedy używać każdego mechanizmu schowka](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [Używanie tradycyjnego interfejsu API Schowka systemu Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)

- [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)

- [Schowek systemu Windows](/windows/win32/dataxchg/clipboard)

- [Implementujące przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
