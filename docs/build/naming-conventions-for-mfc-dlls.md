---
title: Konwencje nazewnictwa bibliotek MFC dll | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC libraries [C++], naming conventions
- naming conventions [C++], MFC DLLs
- MFC DLLs [C++], naming conventions
- libraries [C++], MFC DLL names
- shared DLL versions [C++]
- DLLs [C++], naming conventions
- DLLs [C++], library names
ms.assetid: 0db9c3f3-87d3-40e8-8964-250f9d2a2209
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f7702e9babcc4769136d6deab63b627f8b09bd4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="naming-conventions-for-mfc-dlls"></a>Konwencje nazewnictwa bibliotek MFC DLL
Biblioteki dll i biblioteki dołączony w MFC wykonaj strukturalnych konwencji nazewnictwa. Ułatwia ustalenie, które biblioteki DLL lub biblioteki powinien być używany w celu, które.  
  
 Biblioteki importu niezbędnych do tworzenia aplikacji lub biblioteki DLL rozszerzenia MFC, używające tych bibliotek DLL ma taką samą nazwę podstawową jak plik DLL, ale mają rozszerzenie nazwy pliku lib.  
  
### <a name="shared-dll-naming-convention"></a>Konwencja nazewnictwa Wspólnej bibliotece DLL  
  
|DLL|Opis|  
|---------|-----------------|  
|MFCx0.DLL|Biblioteki MFC DLL wersji ANSI|  
|MFCx0U.DLL|Biblioteki MFC DLL wersji Unicode|  
|MFCx0D.DLL|Biblioteki MFC DLL wersja do debugowania ANSI|  
|MFCx0UD.DLL|Biblioteki MFC DLL wersji do debugowania kodu Unicode|  
  
 Możesz dynamicznie łączenia z udostępnionego wersja biblioteki DLL MFC, czy z aplikacji lub z biblioteki DLL rozszerzenia MFC, musi zawierać MFCx0.DLL z produktem. Jeśli potrzebujesz obsługi formatu Unicode w aplikacji, należy uwzględnić MFCx0U.DLL.  
  
 Jeśli łączysz statycznie bibliotekę DLL z MFC, należy połączyć za pomocą jednej z bibliotek statycznych MFC. Te wersje są nazywane zgodnie z Konwencją [N &#124; U] AFXCW [D]. LIB. Aby uzyskać więcej informacji, zobacz tabelę "Konwencje nazewnictwa bibliotek statyczne łącze" w [konwencje nazewnictwa bibliotek](../mfc/library-naming-conventions.md) (MFC).  
  
 Lista Visual mogą być dystrybuowane za pomocą aplikacji biblioteki dll w języku C++ Zobacz Redist.txt w instalacji programu Visual Studio.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Konwencja nazewnictwa bibliotek](../mfc/library-naming-conventions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)