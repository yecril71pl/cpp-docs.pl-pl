---
title: "Kompilatora (poziom 1) ostrzeżenie C4657 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4657
dev_langs: C++
helpviewer_keywords: C4657
ms.assetid: eb750050-cea6-4ead-b80c-d5dcd4971cfc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cfe2a392de655fdc5340f22784fcd5763e79ff56
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4657"></a>Kompilator C4657 ostrzegawcze (poziom 1)
wyrażenie zawiera typ danych, który jest nowy od czasu ostatniej kompilacji  
  
 Dodać lub zmienić typu danych, dzięki czemu nowy kod źródłowy od momentu ostatniej zakończonej pomyślnie kompilacji. Edytuj i Kontynuuj nie obsługuje zmian do istniejących typów danych.  
  
 To ostrzeżenie będzie zawsze występować [krytyczny błąd C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Aby usunąć to ostrzeżenie bez przerywania bieżącej sesji debugowania  
  
1.  Zmień typ danych do stanu sprzed rozpoczęcia błędu.  
  
2.  Z **debugowania** menu, wybierz **zastosowanie zmian kodu**.  
  
### <a name="to-remove-this-error-without-changing-your-source-code"></a>Aby usunąć ten błąd, bez konieczności zmieniania kodu źródłowego  
  
1.  Z **debugowania** menu, wybierz **Zatrzymaj debugowanie**.  
  
2.  Z **kompilacji** menu, wybierz **kompilacji**.