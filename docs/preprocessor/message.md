---
title: komunikat | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- message_CPP
- vc-pragma.message
dev_langs:
- C++
helpviewer_keywords:
- message pragma
- pragmas, message
ms.assetid: 67414f25-ed47-4079-a5dc-21d9d1a39754
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb998ef084f259601478ea9614a2bd8dc3da0d68
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="message"></a> — komunikat
Wysyła ciąg literału do wyjścia standardowego bez przerywania kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#pragma message( messagestring )  
```  
  
## <a name="remarks"></a>Uwagi  
 Typowy sposób użycia protokołu **komunikat** pragma są wyświetlane komunikaty informacyjne w czasie kompilacji.  
  
 *Messagestring* parametr może być makrem rozwijany do literału ciągu i można łączyć ze sobą takie makra z literał ciągu w dowolnej kombinacji.  
  
 Jeśli używasz wstępnie zdefiniowanego makra w **komunikat** pragma, makra powinien zwrócić ciąg, przeciwnym razie trzeba będzie dane wyjściowe makra jest skonwertowana do ciągu.  
  
 Poniższy fragment kodu używa **komunikat** pragma, aby wyświetlić komunikaty podczas kompilacji:  
  
```  
// pragma_directives_message1.cpp  
// compile with: /LD  
#if _M_IX86 >= 500  
#pragma message("_M_IX86 >= 500")  
#endif  
  
#pragma message("")  
  
#pragma message( "Compiling " __FILE__ )   
#pragma message( "Last modified on " __TIMESTAMP__ )  
  
#pragma message("")  
  
// with line number  
#define STRING2(x) #x  
#define STRING(x) STRING2(x)  
  
#pragma message (__FILE__ "[" STRING(__LINE__) "]: test")  
  
#pragma message("")  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Dyrektywy pragma i słowo kluczowe __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)