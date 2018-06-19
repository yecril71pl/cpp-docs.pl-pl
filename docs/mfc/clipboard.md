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
ms.openlocfilehash: f2ad21bcbff31335f6ec79a4527ef7d99e07e547
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341107"
---
# <a name="clipboard"></a>Schowek
Tej rodziny artykuły omówiono implementuje obsługę Schowka systemu Windows w aplikacjach MFC. Schowka systemu Windows jest używany na dwa sposoby:  
  
-   Implementowanie standardowych poleceń menu Edycja, takich jak wycinania, kopiowania i wklejania.  
  
-   Implementacja uniform danych transfer z przeciąganie i upuszczanie (OLE).  
  
 Schowek jest standard Windows metody transferu danych między źródłem a miejscem docelowym. Może być również przydatne w przypadku operacji OLE. Pojawienie OLE istnieją dwa mechanizmy Schowka systemu Windows. Standardowy interfejs API schowka systemu Windows jest nadal dostępne, ale ma zostały uzupełnione z mechanizmem OLE transferu danych. Transfer danych uniform OLE (UDT) obsługuje wycinania, kopiowania i wklejania ze Schowka i przeciągnij i upuść.  
  
 Schowek jest usługa systemowa współużytkowane przez całej sesji systemu Windows, więc nie ma uchwytu lub jego własnej klasy. Zarządzanie Schowka za pomocą funkcji elementów członkowskich klasy [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Kiedy korzystać z mechanizmu Schowka](../mfc/clipboard-when-to-use-each-clipboard-mechanism.md)  
  
-   [Przy użyciu tradycyjnych interfejs API schowka systemu Windows](../mfc/clipboard-using-the-windows-clipboard.md)  
  
-   [Korzystanie z mechanizmu Schowka OLE](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)  
  
-   [Kopiowanie i wklejanie danych](../mfc/clipboard-copying-and-pasting-data.md)  
  
-   [Dodawanie innych formatów](../mfc/clipboard-adding-other-formats.md)  
  
-   [Schowka systemu Windows](https://msdn.microsoft.com/library/ms648709)  
  
-   [Implementowanie przeciąganie i upuszczanie (OLE)](../mfc/drag-and-drop-ole.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
