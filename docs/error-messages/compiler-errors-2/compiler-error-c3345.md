---
title: "C3345 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3345
dev_langs: C++
helpviewer_keywords: C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ca51e90d8c0cbb1806cc0b042d9c3ae2480a9729
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3345"></a>C3345 błąd kompilatora
"identyfikator": nieprawidłowy identyfikator dla nazwy modułu  
  
 *Identyfikator* dla modułu zawiera jeden lub więcej znaków nie do przyjęcia. Identyfikator jest nieprawidłowy, jeśli pierwszy znak jest alfabetyczne, podkreślenia, lub wysokiej znaków ANSI (0x80 FF) i kolejnych znaków alfanumerycznych podkreślenia lub wysokie znaków ANSI.  
  
### <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Upewnij się, że *identyfikator* nie zawiera spacji lub innych niedopuszczalne znaki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu powoduje błąd C3345, ponieważ `name` parametr `module` atrybut zawiera puste.  
  
```  
// cpp_attr_name_module.cpp  
// compile with: /LD /link /OPT:NOREF  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
// C3345 expected  
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]   
// Try the following line instead  
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]   
// Module attribute now applies to this class  
class CMyClass {  
public:  
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {  
   // add your own code here  
   return __super::DllMain(dwReason, lpReserved);  
   }  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [__iscsym —](../../c-runtime-library/reference/iscsym-functions.md)   
 [Klasyfikacja znaków](../../c-runtime-library/character-classification.md)   
 [Moduł](../../windows/module-cpp.md)