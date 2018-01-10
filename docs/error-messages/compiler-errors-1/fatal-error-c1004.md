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
ms.workload: cplusplus
ms.openlocfilehash: 528147eceadd35cc0d9fe656bdc7ce7965339a0a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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