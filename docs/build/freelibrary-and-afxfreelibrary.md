---
title: FreeLibrary i AfxFreeLibrary | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs: C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3d5f2c1cce980f97e7a99ff2347daceac05f984f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary i AfxFreeLibrary
Procesy, które jawnie link do wywołania DLL [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188) działać, jeśli moduł biblioteki DLL nie jest już potrzebne. To funkcja zmniejsza liczbę odwołanie do modułu i jeśli liczba odwołań wynosi zero, usuwa ją z przestrzeni adresowej procesu mapowanie.  
  
 W aplikacji MFC, użyj [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) zamiast `FreeLibrary` można zwolnić bibliotekę DLL rozszerzenia MFC. Interfejs (prototypu funkcji) dla `AfxFreeLibrary` jest taka sama jak `FreeLibrary`.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Jak połączyć niejawnie z biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Określić jakiej metody łączenia użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)