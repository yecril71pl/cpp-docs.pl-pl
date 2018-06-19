---
title: Relacja z interfejsem API języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d06c4adfa5493929a24c233fa923451c7bf0f95
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33379232"
---
# <a name="relationship-to-the-c-language-api"></a>Relacja z interfejsem API języka C
Jedna właściwość, która ustawia biblioteki Microsoft Foundation Class (MFC) oprócz innych bibliotek klas dla systemu Windows jest bardzo Zamknij mapowania do interfejsu API systemu Windows w języku C. Ponadto można zwykle łączyć wywołania do biblioteki klas za darmo bezpośrednie wywołania interfejsu API systemu Windows. Dostęp bezpośredni, jednak oznacza, że klasy są całkowite zastąpienie dla tego interfejsu API. Deweloperzy muszą nadal sporadycznie bezpośrednich wywołań do niektórych funkcji systemu Windows, takich jak [SetCursor](http://msdn.microsoft.com/library/windows/desktop/ms648393) i [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385), np. Funkcja systemu Windows jest opakowane przez funkcji członkowskiej klasy tylko wtedy, gdy ma wyczyść dodatkowych zalet w ten sposób.  
  
 Ponieważ czasami konieczne jest wprowadzenie macierzystych wywołań funkcji systemu Windows, należy mieć dostęp do dokumentacji interfejsu API systemu Windows w języku C. Niniejsza dokumentacja jest dołączana do pakietu Microsoft Visual C++.  
  
> [!NOTE]
>  Omówienie sposób działania w ramach biblioteki MFC, zobacz [pisać aplikacje dla systemu Windows za pomocą klasy](../mfc/using-the-classes-to-write-applications-for-windows.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ogólne zasady projektowania klas](../mfc/general-class-design-philosophy.md)
