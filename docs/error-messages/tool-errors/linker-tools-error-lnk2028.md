---
title: "Błąd narzędzi konsolidatora LNK2028 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2028
dev_langs: C++
helpviewer_keywords: LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 06865e305e8c87d6a3b4bb74b7b1c7dae7cd45a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk2028"></a>Błąd narzędzi konsolidatora LNK2028
"exported_function" (decorated_name) przywoływany w funkcji "function_containing_function_call" (decorated_name)  
  
 Podczas próby importowanie funkcji macierzystej czysty obraz, należy pamiętać, że niejawne konwencji wywoływania różnią się w kompilacjach kodu natywnego i czysty.  
  
## <a name="example"></a>Przykład  
 Ten przykładowy kod generuje składnika z funkcją wyeksportowany, natywnego, których Konwencja wywoływania jest niejawnie [__cdecl](../../cpp/cdecl.md).  
  
```  
// LNK2028.cpp  
// compile with: /LD  
__declspec(dllexport) int func() {  
   return 3;  
}  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie tworzone czysty klienta, który używa funkcji macierzystej. Jednak Konwencja wywoływania w obszarze **/CLR: pure** jest [__clrcall](../../cpp/clrcall.md). Poniższy przykład generuje LNK2028.  
  
```  
// LNK2028_b.cpp  
// compile with: /clr:pure lnk2028.lib  
// LNK2028 expected  
int func();  
  
int main() {  
   return func();  
}  
```