---
title: "Błąd krytyczny NMAKE U1033 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: U1033
dev_langs: C++
helpviewer_keywords: U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 94f2626e1ce318d83d306595e386f880c62dec3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="nmake-fatal-error-u1033"></a>Błąd krytyczny NMAKE U1033
Błąd składniowy: "string" Nieoczekiwany  
  
 Ciąg nie jest częścią nieprawidłowa składnia dla pliku reguł programu make.  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny  
  
1.  Jeśli zestaw zamykającego nawiasu ostrego (**<<**) dla pliku wbudowanego nie są na początku wiersza, wystąpił następujący błąd:  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  Jeśli elementem definicji makra w pliku reguł programu make zawiera znak równości (**=**) bez poprzedzających nazw lub jeśli nazwa definiowany jest makrem rozwijający na wartość nothing, wystąpił następujący błąd:  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  Jeśli średnik (**;**) w wierszu komentarza, w menu Narzędzia. INI nie jest na początku wiersza, wystąpił następujący błąd:  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  Jeśli plik makefile został sformatowany przy użyciu edytora tekstu, może wystąpić następujący błąd:  
  
    ```  
    syntax error : ':' unexpected  
    ```