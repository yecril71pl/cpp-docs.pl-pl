---
title: "Relacja z interfejsem API języka C | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.mfc
dev_langs:
- C++
helpviewer_keywords:
- books [MFC], about MFC and Windows SDK
- books [MFC]
- MFC, Windows API
- Visual C, Windows API calls
- Windows API [MFC], and MFC
ms.assetid: 334e8efc-f3cc-4018-bc2e-02908b2a39fe
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26458242ab6afcf69d6e70065ba70e31f0adbe74
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="relationship-to-the-c-language-api"></a>Relacja z interfejsem API języka C
Jedna właściwość, która ustawia biblioteki Microsoft Foundation Class (MFC) oprócz innych bibliotek klas dla systemu Windows jest bardzo Zamknij mapowania do interfejsu API systemu Windows w języku C. Ponadto można zwykle łączyć wywołania do biblioteki klas za darmo bezpośrednie wywołania interfejsu API systemu Windows. Dostęp bezpośredni, jednak oznacza, że klasy są całkowite zastąpienie dla tego interfejsu API. Deweloperzy muszą nadal sporadycznie bezpośrednich wywołań do niektórych funkcji systemu Windows, takich jak [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) i [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), np. Funkcja systemu Windows jest opakowane przez funkcji członkowskiej klasy tylko wtedy, gdy ma wyczyść dodatkowych zalet w ten sposób.  
  
 Ponieważ czasami konieczne jest wprowadzenie macierzystych wywołań funkcji systemu Windows, należy mieć dostęp do dokumentacji interfejsu API systemu Windows w języku C. Niniejsza dokumentacja jest dołączana do pakietu Microsoft Visual C++.  
  
> [!NOTE]
>  Omówienie sposób działania w ramach biblioteki MFC, zobacz [pisać aplikacje dla systemu Windows za pomocą klasy](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne zasady projektowania klas](../mfc/general-class-design-philosophy.md)
