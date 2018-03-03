---
title: "Wyszukaj ścieżkę używaną przez system Windows do lokalizowania biblioteki DLL | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- searching [C++], DLLs
- DLLs [C++], Windows search path
- Windows [C++], DLL search path
- known DLL searches [C++]
- locating DLLs
- finding DLLs
- search paths [C++]
ms.assetid: 84bfb380-ad7b-4962-b2d0-51b19a45f1bb
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 53350ed473226c86dd4fefa93cff376a371dedf7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="search-path-used-by-windows-to-locate-a-dll"></a>Ścieżka wyszukiwania używana przez system Windows do lokalizowania biblioteki DLL
Z łączenie jawne i niejawne, systemu Windows najpierw szuka "znanych DLLs", takie jak Kernel32.dll i User32.dll. System Windows wyszukuje dla bibliotek DLL w następującej kolejności:  
  
1.  Katalog, w którym znajduje się moduł pliku wykonywalnego dla bieżącego procesu.  
  
2.  Bieżący katalog.  
  
3.  Katalog systemu Windows. **GetSystemDirectory** funkcja pobiera ścieżki tego katalogu.  
  
4.  Katalog systemu Windows. **GetWindowsDirectory** funkcja pobiera ścieżki tego katalogu.  
  
5.  Katalogi wymienione w zmiennej środowiskowej PATH.  
  
    > [!NOTE]
    >  Libpath-zmienna środowiskowa nie jest używany.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Jak połączyć niejawnie z biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Jak połączyć jawnie z biblioteki DLL](../build/linking-an-executable-to-a-dll.md#linking-explicitly)  
  
-   [Określić jakiej metody łączenia użyć](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteki DLL w programie Visual C++](../build/dlls-in-visual-cpp.md)