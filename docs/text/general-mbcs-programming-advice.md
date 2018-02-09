---
title: "Porady dotyczące programowania MBSC ogólne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b379c163963a9ae0dd0c59c7d0fc809fee4f46d0
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="general-mbcs-programming-advice"></a>Ogólne porady dotyczące programowania MBSC
Użyj następujących wskazówek:  
  
-   Elastyczność, użyj makra czasu wykonywania takich jak `_tcschr` i `_tcscpy` Jeśli to możliwe. Aby uzyskać więcej informacji, zobacz [mapowania zwykłego tekstu w pliku Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Użyj C-run-time `_getmbcp` funkcji, aby uzyskać informacje o bieżącej stronie kodowej.  
  
-   Nie należy używać ponownie zasobów ciągu. W zależności od języka docelowego dany ciąg znaków może mieć inne znaczenie podczas translacji. Na przykład głównego menu "File" dla aplikacji może tłumaczyć inaczej z ciągu "File" w oknie dialogowym. Jeśli musisz użyć więcej niż jeden ciąg o takiej samej nazwie, użyj ciągu różne identyfikatory dla każdego.  
  
-   Możesz sprawdzić, czy aplikacja jest uruchomiona w systemie operacyjnym włączone MBCS. Aby to zrobić, należy ustawić flagę w momencie uruchamiania programu; nie należy polegać na wywołania interfejsu API.  
  
-   Podczas projektowania okien dialogowych, Zezwalaj na około 30% dodatkowe miejsce na końcu tekst statyczny kontrolki MBCS tłumaczenia.  
  
-   Należy zachować ostrożność, wybierając czcionki dla danej aplikacji, ponieważ niektóre czcionki nie są dostępne we wszystkich systemach.  
  
-   Podczas wybierania czcionki dla okien dialogowych, użyj [MS Shell Dlg](http://msdn.microsoft.com/library/windows/desktop/dd374112) zamiast MS Sans Serif lub Helvetica. MS Shell Dlg zastępuje poprawną czcionkę systemu przed utworzeniem okna dialogowego. Korzystanie z MS Shell Dlg zapewnia wszystkie zmiany w systemie operacyjnym na wypadek tę czcionkę automatycznie będą dostępne. (MFC zastępuje MS Shell Dlg DEFAULT_GUI_FONT lub czcionki systemowej w systemie Windows 95, Windows 98 i 4 systemu Windows NT, ponieważ te systemy nie obsługują poprawnie MS Shell Dlg.)  
  
-   Podczas projektowania aplikacji, należy podjąć decyzję ciągów, które może być lokalizowany. W razie wątpliwości założono będzie lokalizowany dowolnego ciągu. W efekcie niemieszanie ciągów, które może być lokalizowany z tymi, które nie.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady dotyczące programowania MBCS](../text/mbcs-programming-tips.md)   
 [Inkrementacja i dekrementacja wskaźników](../text/incrementing-and-decrementing-pointers.md)