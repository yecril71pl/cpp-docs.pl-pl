---
title: Kompilatora (poziom 1) ostrzeżenie C4655 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4655
dev_langs:
- C++
helpviewer_keywords:
- C4655
ms.assetid: 540f2c7a-e4a1-49af-84b4-03eeea1bbf41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6011bf3a2a3bf1718fc15823f2541f49306857c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4655"></a>Kompilator C4655 ostrzegawcze (poziom 1)
**'**   
 ***symbol* ": typ zmiennej jest nowy od czasu ostatniej kompilacji lub jest zdefiniowany w różny sposób w innym miejscu**  
  
 Zmienić lub dodać nowy typ danych od czasu ostatniej zakończonej pomyślnie kompilacji. Edytuj i Kontynuuj nie obsługuje zmian do istniejących typów danych.  
  
 To ostrzeżenie występuje [krytyczny błąd C1092](../../error-messages/compiler-errors-1/fatal-error-c1092.md). Aby uzyskać więcej informacji, zobacz [obsługiwane zmiany kodu](/visualstudio/debugger/supported-code-changes-cpp).  
  
### <a name="to-remove-this-warning-without-ending-the-current-debug-session"></a>Aby usunąć to ostrzeżenie bez przerywania bieżącej sesji debugowania  
  
1.  Zmień typ danych do stanu sprzed rozpoczęcia błędu.  
  
2.  Z **debugowania** menu, wybierz **zastosowanie zmian kodu**.  
  
### <a name="to-remove-this-warning-without-changing-your-source-code"></a>Aby usunąć to ostrzeżenie, bez konieczności zmieniania kodu źródłowego  
  
1.  Z **debugowania** menu, wybierz **Zatrzymaj debugowanie**.  
  
2.  Z **kompilacji** menu, wybierz **kompilacji**.