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
ms.openlocfilehash: 5f4a17bedaa50913dce1f6388dfb6b8d9ecd38da
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617285"
---
# <a name="clipboard"></a>Schowek

W tej rodzinie artykułów wyjaśniono, jak zaimplementować obsługę Schowka systemu Windows w aplikacjach MFC. Schowek systemu Windows jest używany na dwa sposoby:

- Implementowanie standardowych poleceń menu edycji, takich jak wycinanie, kopiowanie i wklejanie.

- Implementowanie jednolitego transferu danych przy użyciu przeciągania i upuszczania OLE.

Schowek jest standardową metodą transferu danych między źródłem a miejscem docelowym. Może być również bardzo przydatne w operacjach OLE. W przypadku pojawieniu OLE istnieją dwa mechanizmy w systemie Windows. Standardowy interfejs API Schowka systemu Windows jest nadal dostępny, ale został uzupełniony mechanizmem transferu danych OLE. Funkcja OLE Uniform Data Transfer (UDT) obsługuje wycinanie, kopiowanie i wklejanie ze schowka i przeciąganie i upuszczanie.

Schowek jest usługą systemową udostępnioną przez całą sesję systemu Windows, więc nie ma własnego dojścia ani klasy. Schowek można zarządzać za pomocą funkcji członkowskich klasy [CWnd](reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Kiedy używać każdego mechanizmu schowka](clipboard-when-to-use-each-clipboard-mechanism.md)

- [Używanie tradycyjnego interfejsu API Schowka systemu Windows](clipboard-using-the-windows-clipboard.md)

- [Korzystanie z mechanizmu Schowka OLE](clipboard-using-the-ole-clipboard-mechanism.md)

- [kopiowanie i wklejanie danych](clipboard-copying-and-pasting-data.md)

- [Dodawanie innych formatów](clipboard-adding-other-formats.md)

- [Schowek systemu Windows](/windows/win32/dataxchg/clipboard)

- [Przeciąganie i upuszczanie elementów OLE](drag-and-drop-ole.md)

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](user-interface-elements-mfc.md)
