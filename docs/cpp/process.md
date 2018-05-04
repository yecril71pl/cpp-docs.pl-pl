---
title: proces | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- process_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8aa1ba2676ebbd04d1fc1a59d210d69efeab6658
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="process"></a>proces
Określa, czy procesu zarządzanej aplikacji powinien mieć pojedynczą kopię określonej zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna współużytkowana przez wszystkie domeny aplikacji w procesie. To przede wszystkim był przeznaczony do użycia podczas kompilowania za pomocą **/CLR: pure**, która jest teraz przestarzałe i zostanie usunięta w przyszłej wersji kompilatora. Podczas kompilowania za pomocą **/CLR**, zmienne globalne i statyczne są na proces domyślnie (nie trzeba używać `__declspec(process)`.  
  
 Tylko zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna typu natywnego może być oznaczony przez `__declspec(process)`.  
  
  
 `process` jest prawidłowy tylko podczas kompilowania za pomocą [/CLR](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Każda domena aplikacji ma własną kopię zmiennej globalnej, należy użyć [elementu appdomain](../cpp/appdomain.md).  
  
 Zobacz [i domen aplikacji Visual C++](../dotnet/application-domains-and-visual-cpp.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)