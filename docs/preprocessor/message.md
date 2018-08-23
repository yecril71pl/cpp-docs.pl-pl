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
ms.openlocfilehash: a3ce9091fe380f7d255dd321dbb9eb5ca7134b8d
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465401"
---
# <a name="message"></a>— komunikat
Wysyła ciąg literału do wyjścia standardowego bez przerywania kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
#pragma message( messagestring )  
```  
  
## <a name="remarks"></a>Uwagi  

Typowym zastosowaniem **komunikat** pragma są wyświetlane komunikaty informacyjne w czasie kompilacji.  
  
*Messagestring* parametr może być — makro, który rozwija do literału ciągu i można połączyć tych makr, za pomocą literałów ciągów w dowolnej kombinacji.  
  
Wstępnie zdefiniowane makra w **komunikat** pragma, makro powinien zwrócenia ciągu, przeciwnym razie trzeba będzie konwertować dane wyjściowe makra do ciągu.  
  
Poniższy fragment kodu używa **komunikat** pragma umożliwiające wyświetlanie komunikatów podczas kompilacji:  
  
```cpp  
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