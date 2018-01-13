---
title: "Porady dotyczące programowania MBCS | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: _mbcs
dev_langs: C++
helpviewer_keywords:
- programming [C++], MBCS
- character sets [C++], multibyte
- MBCS [C++], programming
- multibyte characters [C++]
ms.assetid: d8ad36b8-917f-474e-8adb-69462adecd17
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1dc9c5dfd0dafe96e2d37b789b64c8215aa454e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mbcs-programming-tips"></a>Porady dotyczące programowania MBCS
W nowo tworzonym należy użyć kodowania znaków Unicode dla wszystkich ciągów, które prawdopodobnie mogą zobaczyć użytkownicy końcowi. MBCS jest technologią starszej wersji, która została zastąpiona Unicode. W tej sekcji udostępnia wskazówki dla deweloperów, którzy muszą zachować istniejące programy, które używają MBCS i których nie jest praktyczne można przekonwertować na ciąg Unicode. Zalecenia dotyczą aplikacji MFC i aplikacji napisanych bez MFC. Tematy obejmują:  
  
-   [Ogólne porady dotyczące programowania MBSC](../text/general-mbcs-programming-advice.md)  
  
-   [Inkrementacja i dekrementacja wskaźników](../text/incrementing-and-decrementing-pointers.md)  
  
-   [Indeksy bajtowe](../text/byte-indices.md)  
  
-   [Ostatni znak w ciągu](../text/last-character-in-a-string.md)  
  
-   [Przypisanie znaku](../text/character-assignment.md)  
  
-   [Porównywanie znaków](../text/character-comparison.md)  
  
-   [Przepełnienie buforu](../text/buffer-overflow.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa zestawów znaków wielobajtowych (zestawy MBCS)](../text/support-for-multibyte-character-sets-mbcss.md)