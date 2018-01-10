---
title: Unicode strumienia I-O w trybach tekstowym i binarnym | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.io
dev_langs: C++
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 76e739ae95788448cc655ca18d32aaf1f8a5c90a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>Strumień We/Wy Unicode w trybach tekstowym i binarnym
Gdy Unicode strumienia procedury we/wy (takich jak `fwprintf`, `fwscanf`, `fgetwc`, `fputwc`, `fgetws`, lub `fputws`) działa na pliku, która jest otwarta w trybie tekstowym (ustawienie domyślne), dwa rodzaje znaków konwersje miejsce:  
  
-   Konwersja Unicode do MBCS lub MBCS na Unicode. Jeśli funkcja strumienia I/O Unicode działa w trybie tekstowym, źródła lub strumień docelowy zakłada, że sekwencja znaków wielobajtowych. W związku z tym funkcji wejścia strumienia Unicode konwertuje znaki wielobajtowe na znaki dwubajtowe (tak jak w przypadku przez wywołanie do `mbtowc` funkcji). Z tego samego powodu funkcje strumieni wyjściowych Unicode przekonwertować znaki dwubajtowe znaków wielobajtowych (tak jak w przypadku przez wywołanie do `wctomb` funkcji).  
  
-   Powrót karetki - tłumaczenia wysuwu wiersza (CR LF). Tłumaczenie występuje przed MBCS — Konwersja Unicode (dla funkcji wejściowych strumienia Unicode) i po Unicode - konwersji MBCS (dla funkcji wyjściowego strumienia Unicode). Podczas wprowadzania danych przez każdego powrotu karetki - kombinacja wysuwu wiersza jest przetłumaczyć znaku pojedynczego wysuwu wiersza. W danych wyjściowych każdy znak wysuwu wiersza jest przetłumaczony na powrót karetki - kombinacja wysuwu wiersza.  
  
 Jednak jeśli funkcja strumienia I/O Unicode działa w trybie binarnym, plik zostanie potraktowany jako Unicode i brak konwersji tłumaczenia lub znak CR LF wypada w danych wejściowych lub wyjściowych. Użyj _setmode — (_fileno — (stdin), _o_binary —); instrukcji, aby można było poprawnie używać wcin w pliku tekstowym UNICODE.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury czasu wykonywania według kategorii](../c-runtime-library/run-time-routines-by-category.md)   
 [Dane wejściowe i wyjściowe](../c-runtime-library/input-and-output.md)