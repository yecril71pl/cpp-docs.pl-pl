---
title: Błąd narzędzi konsolidatora LNK2028 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2028
dev_langs:
- C++
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7347e8edda7ad8b317d4e6e02dfc9345ac76f269
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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