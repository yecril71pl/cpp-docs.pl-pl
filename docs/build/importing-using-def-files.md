---
title: "Importowanie przy użyciu plików DEF | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- importing DLLs [C++], DEF files
- def files [C++], importing with
- .def files [C++], importing with
- dllimport attribute [C++], DEF files
- DLLs [C++], DEF files
ms.assetid: aefdbf50-f603-488a-b0d7-ed737bae311d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 81148525b70f3c5ff351feb9561699f3b9b5e932
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="importing-using-def-files"></a>Importowanie przy użyciu plików DEF
Jeśli chcesz użyć **__declspec(dllimport)** wraz z plikiem .def należy zmienić plik .def, aby użyć danych zamiast STAŁA, aby zmniejszyć prawdopodobieństwo, że nieprawidłowe kodowanie spowoduje, że problem:  
  
```  
// project.def  
LIBRARY project  
EXPORTS  
   ulDataInDll   DATA  
```  
  
 W poniższej tabeli przedstawiono przyczyny.  
  
|Słowo kluczowe|Emituje biblioteki importu|Eksporty|  
|-------------|---------------------------------|-------------|  
|`CONSTANT`|`_imp_ulDataInDll`, `_ulDataInDll`|`_ulDataInDll`|  
|`DATA`|`_imp_ulDataInDll`|`_ulDataInDll`|  
  
 Przy użyciu **__declspec(dllimport)** i STAŁA listy zarówno `imp` wersji i bez nazwy w .lib DLL zaimportować bibliotekę, która jest tworzona umożliwiają łączenie jawne. Przy użyciu **__declspec(dllimport)** i listę danych tylko `imp` wersja nazwy.  
  
 Jeśli używasz STAŁĄ, albo następujące konstrukcje kodu może służyć do dostępu `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll; /*prototype*/  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 —lub—  
  
```  
ULONG *ulDataInDll;      /*prototype*/  
if (*ulDataInDll == 0L)  /*sample code fragment*/  
```  
  
 Jednak jeśli używasz danych w pliku .def tylko kodu skompilowanego za pomocą następującej definicji mają dostęp do zmiennej `ulDataInDll`:  
  
```  
__declspec(dllimport) ULONG ulDataInDll;  
  
if (ulDataInDll == 0L)   /*sample code fragment*/  
```  
  
 Używanie STAŁA jest bardziej ryzykowne, ponieważ Jeśli zapomnisz dodatkowy poziom pośredni, może potencjalnie dostęp tabelę adresów importu wskaźnik do zmiennej — nie zmiennej. Tego rodzaju problem można często manifeście jako naruszenia zasad dostępu, ponieważ tabelę adresów importu jest obecnie tylko do odczytu w kompilatorze i konsolidatorze.  
  
 Bieżący konsolidatora Visual C++ wygeneruje ostrzeżenie, jeśli STAŁA w pliku .def dla tej sprawy. Tylko rzeczywista Przyczyna do użycia STAŁA jest, jeśli nie można ponownie skompilować niektóre pliku obiektu, gdy plik nagłówka nie listy **__declspec(dllimport)** na prototypu.  
  
## <a name="see-also"></a>Zobacz też  
 [Importowanie do aplikacji](../build/importing-into-an-application.md)
