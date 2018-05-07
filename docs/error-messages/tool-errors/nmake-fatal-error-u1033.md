---
title: Błąd krytyczny NMAKE U1033 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1033
dev_langs:
- C++
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1d39d4c35ec66d405d51d601b7c5d2b2ab37b02
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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