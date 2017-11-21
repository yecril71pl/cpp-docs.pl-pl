---
title: "Eksportowanie funkcji z biblioteki DLL według liczby porządkowej, a nie nazwa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NONAME
dev_langs: C++
helpviewer_keywords:
- exporting functions [C++], ordinal values
- ordinal exports [C++]
- exporting DLLs [C++], ordinal values
- NONAME attribute
ms.assetid: 679719fd-d965-4df3-9f7a-7d86ad831702
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4d5420a426f0dc1244ede19fc4abddf56469608d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="exporting-functions-from-a-dll-by-ordinal-rather-than-by-name"></a>Eksportowanie funkcji z biblioteki DLL według numeru porządkowego a nie nazwy
Najprostszym sposobem, aby wyeksportować funkcji z biblioteki DLL jest wyeksportować je według nazwy. Jest to, co się dzieje, gdy używasz **__declspec(dllexport)**, np. Ale zamiast tego można wyeksportować funkcji według liczby porządkowej. W przypadku tej techniki, należy użyć pliku .def zamiast **__declspec(dllexport)**. Aby określić wartość porządkową funkcji, należy dołączyć jego liczby porządkowej nazwa funkcji w pliku .def. Informacje o określaniu porządkowe, zobacz [eksportowanie z biblioteki DLL przy użyciu .def — pliki](../build/exporting-from-a-dll-using-def-files.md).  
  
> [!TIP]
>  Jeśli chcesz zoptymalizować rozmiar pliku biblioteki DLL, użyj **NONAME** atrybutu na każdym wyeksportowanej funkcji. Z **NONAME** atrybutu porządkowe są przechowywane w DLL Eksportowanie tabeli, a nie nazwy funkcji. Może to być znaczne oszczędności, eksportowania wiele funkcji.  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
-   [Używany plik .def, więc można wyeksportować według liczby porządkowej](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [Użyj __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Eksportowanie z biblioteki DLL](../build/exporting-from-a-dll.md)