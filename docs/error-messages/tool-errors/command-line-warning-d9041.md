---
title: Ostrzeżenie D9041 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9041
dev_langs:
- C++
helpviewer_keywords:
- D9041
ms.assetid: ada8815f-4246-4e25-b57d-a7f16fa107cc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c22573d26e09e14789f4cbd64d68f4082125c2b3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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