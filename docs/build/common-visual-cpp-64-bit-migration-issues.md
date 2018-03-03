---
title: "Typowe problemy przy migracji 64-bitowe języka Visual C++ | Dokumentacja firmy Microsoft"
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
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b9ea3690e04106f0836d236eefee4acd9dda3a82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Typowe problemy przy migracji Visual C++ w wersji 64-bitowej

Korzystając z programu Visual C++ do tworzenia aplikacji do uruchomienia w 64-bitowym systemie operacyjnym Windows, należy pamiętać o następujących problemów:  
  
-   `int` i `long` wartości 32-bitowych na 64-bitowych systemach operacyjnych Windows. Dla programów, które planujesz do kompilowania dla platformy 64-bitowych należy zachować ostrożność nie przypisać wskaźników do zmiennych 32-bitowych. Wskaźniki są 64-bit na platformach 64-bitowych i obetnie wartość wskaźnika, jeśli można przypisać do zmiennej 32-bitowych.  
  
-   `size_t`, `time_t`, i `ptrdiff_t` wartości 64-bitowym na 64-bitowych systemach operacyjnych Windows.  
  
-   `time_t`jest to wartość 32-bitowego w 32-bitowych systemach operacyjnych Windows w wersjach programu Visual C++ przed Visual C++ 2005. `time_t`jest teraz 64-bitową liczbę całkowitą domyślnie. Aby uzyskać więcej informacji, zobacz [zarządzanie czasem](../c-runtime-library/time-management.md).  
  
     Należy zwrócić uwagę w przypadku gdy ma kod `int` wartość i przetwarza je jako `size_t` lub `time_t` wartość. Jest możliwe, że liczba wzrostu może być większe niż 32-bitową liczbą i dane zostaną obcięte podczas jego jest przekazywane z powrotem do `int` magazynu.  
  
%X (szesnastkowo `int` format) `printf` modyfikator nie będzie działać zgodnie z oczekiwaniami w 64-bitowym systemie operacyjnym Windows. Działa tylko na pierwszym 32 bity wartość, która została przekazana do niej.  
  
-   % I32x umożliwia wyświetlanie 32-bitowego typu całkowitego w formacie szesnastkowym.  
  
-   % I64x umożliwia wyświetlanie 64-bitowego typu całkowitego w formacie szesnastkowym.  
  
-   %P (w formacie szesnastkowym dla wskaźnika) będą działać zgodnie z oczekiwaniami w 64-bitowym systemie operacyjnym Windows.  
  
Aby uzyskać więcej informacji, zobacz:  
  
-   [Opcje kompilatora](../build/reference/compiler-options.md)  
  
-   [Wskazówki dotyczące migracji](http://msdn.microsoft.com/library/windows/desktop/aa384214)  
  
## <a name="see-also"></a>Zobacz też  

[Visual C++ for x64 64-bitowy, konfigurowanie obiektów docelowych](../build/configuring-programs-for-64-bit-visual-cpp.md)   
[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)