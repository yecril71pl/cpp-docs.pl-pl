---
title: Schowek | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cutting and copying data
- copying data
- Clipboard
- Clipboard, programming
- transferring data
ms.assetid: a71b2824-1f14-4914-8816-54578d73ad4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 48315b3608a5e66c2f94e1b06a038772dbb25bb4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46380493"
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

## <a name="see-also"></a>Zobacz też

[Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
