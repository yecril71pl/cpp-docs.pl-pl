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
ms.openlocfilehash: 4fcf53f1d861a85d830d0fb4244e8af9c11af163
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293293"
---
# <a name="clipboard"></a>Schowek

Tej rodziny artykuły wyjaśnia, jak zaimplementować obsługę Windows Schowka w aplikacjach MFC. Schowek Windows jest używany na dwa sposoby:

- Implementowanie standardowych poleceń menu edycji, takich jak wycinanie, kopiowanie i wklejanie.

- Implementowanie jednolitego dane transferu za pomocą przeciągania i upuszczanie (OLE).

Schowek jest standardowa metoda Windows przesyłania danych między źródłem i miejscem docelowym. Również może być bardzo przydatne w przypadku operacji OLE. Pojawienie OLE istnieją dwa mechanizmy Schowka w Windows. Standardowy interfejs API Schowka Windows jest nadal dostępna, ale ma został uzupełniony z mechanizmem OLE transferu danych. Transfer danych jednolitego OLE (UDT) obsługuje wycinanie, kopiowanie i wklejanie ze Schowka i przeciągnij i upuść.

Schowek jest współużytkowane przez całą sesję Windows, więc nie ma uchwytu lub jego własnej klasy usługi systemowej. Zarządzanie Schowka za pomocą funkcji elementów członkowskich klasy [CWnd](../mfc/reference/cwnd-class.md).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Kiedy należy korzystać z mechanizmu Schowka](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)

- [Przy użyciu tradycyjnych API Schowka Windows](../mfc/clipboard-using-the-windows-clipboard.md)

- [Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

- [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)

- [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)

- [Schowek Windows](https://msdn.microsoft.com/library/ms648709)

- [Implementowanie przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)

## <a name="see-also"></a>Zobacz także

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
