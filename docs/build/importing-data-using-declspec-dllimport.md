---
title: "Importowanie danych przy użyciu atrybutu __declspec(dllimport) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- dllimport
dev_langs:
- C++
helpviewer_keywords:
- importing data [C++]
- dllimport attribute [C++], data imports
- __declspec(dllimport) keyword [C++]
- importing DLLs [C++], __declspec(dllimport)
ms.assetid: 0ae70b39-87c7-4181-8be9-e786e0db60b0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ebbc91b9144a7fe8025a34e9c1476ab23b604c46
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="importing-data-using-declspecdllimport"></a>Importowanie danych przy użyciu atrybutu __declspec(dllimport)
W przypadku danych przy użyciu **__declspec(dllimport)** jest elementem wygody, która usuwa warstwa pośrednia. Podczas importowania danych z biblioteki DLL, musisz przejść przez tabelę adresów importu. Przed **__declspec(dllimport)**, oznacza to pamiętaj, aby wykonać dodatkowy poziom pośredni podczas uzyskiwania dostępu do danych eksportu z biblioteki DLL:  
  
```  
// project.h  
#ifdef _DLL   // If accessing the data from inside the DLL  
   ULONG ulDataInDll;  
  
#else         // If accessing the data from outside the DLL  
   ULONG *ulDataInDll;  
#endif  
```  
  
 Następnie będzie eksportować dane w sieci. Plik DEF:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   CONSTANT  
```  
  
 i uzyskać do niego dostęp spoza biblioteki DLL:  
  
```  
if (*ulDataInDll == 0L)   
{  
   // Do stuff here  
}  
```  
  
 Po oznaczeniu danych jako **__declspec(dllimport)**, kompilator automatycznie generuje kod pośredni dla Ciebie. Nie musisz już martwić się o powyższe kroki. Jak wspomniano wcześniej, nie używaj **__declspec(dllimport)** deklaracji danych podczas tworzenia biblioteki DLL. Funkcje w obrębie biblioteki DLL nie używaj tabelę adresów importu dostępu do obiektu danych; w związku z tym nie należy dodatkowy poziom pośredni obecny.  
  
 Aby wyeksportować dane automatycznie z biblioteki DLL, należy użyć tej deklaracji:  
  
```  
__declspec(dllexport) ULONG ulDataInDLL;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie do aplikacji](../build/importing-into-an-application.md)