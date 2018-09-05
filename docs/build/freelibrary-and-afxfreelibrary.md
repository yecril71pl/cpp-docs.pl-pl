---
title: FreeLibrary i AfxFreeLibrary | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- FreeLibrary
- AfxFreeLibrary
dev_langs:
- C++
helpviewer_keywords:
- extension DLLs [C++], unloading
- AfxFreeLibrary method
- unloading DLLs
- FreeLibrary method
- DLLs [C++], linking
- explicit linking [C++]
- DLLs [C++], unloading
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 063c858253c12cfedbf252a124029b8cbc16a691
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43680966"
---
# <a name="freelibrary-and-afxfreelibrary"></a>FreeLibrary i AfxFreeLibrary
Procesy, które jawnie utworzyć łącze do wywołania biblioteki DLL [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx) działa, gdy moduł DLL nie jest już potrzebny. Ta funkcja zmniejsza liczbę odwołań modułu i jeśli licznik odwołań wynosi zero, unmaps go z przestrzeni adresowej procesu.  
  
 W aplikacji MFC, należy użyć [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary) zamiast `FreeLibrary` wyładować bibliotekę DLL rozszerzenia MFC. Interfejs (prototyp funkcji) `AfxFreeLibrary` jest taka sama jak `FreeLibrary`.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Jak połączyć niejawnie biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Określić, której metody łączenia użyjesz](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
-   [LoadLibrary i AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki dll w programie Visual C++](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152(v=vs.85).aspx)   
 [AfxFreeLibrary](../mfc/reference/application-information-and-management.md#afxfreelibrary)