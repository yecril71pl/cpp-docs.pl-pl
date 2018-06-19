---
title: komunikat | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47b9fd580d1ebabf4352104fe49f1d3c982a49e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846366"
---
# <a name="message"></a>— komunikat
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