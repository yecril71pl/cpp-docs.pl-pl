---
title: Niszczenie okien ramowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PostNcDestroy
dev_langs: C++
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0ab4e9999b46bc005f377b51c691f6947519143e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="destroying-frame-windows"></a>Niszczenie okien ramowych
Struktura MFC zarządza zniszczenie okna, a także tworzenie tych Windows skojarzone z framework dokumentów i widoków. Jeśli utworzysz dodatkowe okna jest odpowiedzialny za zniszczenia.  
  
 W ramach, gdy użytkownik zamyka okno ramowe domyślne okna [OnClose](../mfc/reference/cwnd-class.md#onclose) wywołań obsługi [DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow). Jest ostatnim funkcji członkowskiej wywoływane, gdy okno systemu Windows zostanie zniszczony [OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy), która działa niektórych oczyszczania wywołuje [domyślne](../mfc/reference/cwnd-class.md#default) elementu członkowskiego funkcja do wykonania oczyszczania systemu Windows, a na koniec wywołuje wirtualnej funkcji członkowskiej [PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy). [Cframewnd —](../mfc/reference/cframewnd-class.md) implementacja `PostNcDestroy` usuwa obiekt window C++. Nigdy nie należy używać języka C++ **usunąć** operatora w oknie ramowym. Zamiast nich należy używać słów kluczowych `DestroyWindow`.  
  
 Po zamknięciu okna głównego, zamyka aplikację. Jeśli zostaną zmodyfikowane niezapisane dokumenty, ramach wyświetla komunikat do żądania, jeśli ma zostać zapisany dokumentów i zapewnia, że odpowiednie dokumenty są zapisywane w razie potrzeby.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie okien ramowych](../mfc/using-frame-windows.md)

