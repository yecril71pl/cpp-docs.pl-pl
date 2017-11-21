---
title: "Błąd krytyczny C1004 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1004
dev_langs: C++
helpviewer_keywords: C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6a9e74d7918e1cb2c9190c87f4f1ec75f89237b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1004"></a>Błąd krytyczny C1004
Nieoczekiwany koniec pliku znaleziono  
  
 Kompilator osiągnięto koniec pliku źródłowego bez rozwiązywania konstrukcję. Kod może brakować jeden z następujących elementów:  
  
-   Zamykający nawias klamrowy  
  
-   Nawias zamykający  
  
-   Znacznik komentarz dotyczący zamknięcia (* /)  
  
-   Średnikami  
  
 Aby rozwiązać ten problem, sprawdź następujące czynności:  
  
-   Na dysku domyślny jest za mało miejsca na pliki tymczasowe, które wymagają o dwa razy więcej miejsca w pliku źródłowym.  
  
-   `#if` Dyrektywy, którego wynikiem jest wartość false nie ma zamknięcia `#endif` dyrektywy.  
  
-   Plik źródłowy nie kończy się znak powrotu karetki i wysuwu wiersza.  
  
 Poniższy przykład generuje C1004:  
  
```  
// C1004.cpp  
#if TEST  
int main() {}  
// C1004  
```  
  
 Możliwe rozwiązanie:  
  
```  
// C1004b.cpp  
#if TEST  
#endif  
  
int main() {}  
```