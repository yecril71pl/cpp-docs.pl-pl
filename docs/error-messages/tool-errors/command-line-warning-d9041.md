---
title: "Ostrzeżenie D9041 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: D9041
dev_langs: C++
helpviewer_keywords: D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9f80de8e9bbbf7c754ac8e13061ef3ae50c4715a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="command-line-warning-d9041"></a>Ostrzeżenie D9041 dla wiersza polecenia
Nieprawidłowa wartość 'value' dla '/ opcja'; Zakładając, że 'value'; Dodaj "/ analyze" do opcji wiersza poleceń podczas określania tego ostrzeżenia  
  
 Dodano numer ostrzeżenia analizy kodu **/wd**, **/we**, **/wo**, lub **/wl** opcji wiersza polecenia bez określenia **/ analyze** opcji wiersza polecenia. Aby rozwiązać ten błąd, Dodaj **/ analyze** wiersza polecenia, lub usuń nieprawidłowy numer ostrzeżenia z odpowiednią **/w** opcji wiersza polecenia.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie polecenie generuje ostrzeżenie D9041:  
  
```  
cl /EHsc /LD /wd6001 filename.cpp  
```  
  
 Aby naprawić tego ostrzeżenia, Dodaj **/ analyze** opcji wiersza polecenia. Jeśli **/ analyze** jest nieobsługiwane w wersji kompilatora i usuń nieprawidłowy numer ostrzeżenia z **/wd** opcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy wiersza polecenia od D8000 do D9999](../../error-messages/tool-errors/command-line-errors-d8000-through-d9999.md)   
 [Opcje kompilatora](../../build/reference/compiler-options.md)