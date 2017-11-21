---
title: proces | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: process_cpp
dev_langs: C++
helpviewer_keywords:
- __declspec keyword [C++], process
- process __declspec keyword
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7d7eaeb62f3d8231d7b1a5bca503cd355f7a7aca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="process"></a>proces
Określa, czy procesu zarządzanej aplikacji powinien mieć pojedynczą kopię określonej zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna współużytkowana przez wszystkie domeny aplikacji w procesie. To przede wszystkim jest przeznaczona do użycia podczas kompilowania za pomocą **/CLR: pure**, ponieważ w obszarze **/CLR: pure** zmienne globalne i statyczne są właściwe dla domeny aplikacji, domyślnie. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015. Podczas kompilowania za pomocą **/CLR**, zmienne globalne i statyczne są na proces domyślnie (nie trzeba używać `__declspec(process)`.  
  
 Tylko zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna typu natywnego może być oznaczony przez `__declspec(process)`.  
  
 Podczas kompilowania za pomocą **/CLR: pure**, Zmienne oznaczone zgodnie z procesem również musi być zadeklarowany jako `const`. Dzięki temu na proces zmienne nie są zmieniane w jednej domenie aplikacji, a nadanie nieoczekiwane wyniki w innej domenie aplikacji. Podstawowy przeznaczenie `__declspec(process)` jest umożliwienie inicjowania czas kompilacji zmiennej globalnej, statycznym elementem członkowskim zmiennej lub statyczna zmienna lokalna w obszarze **/CLR: pure**.  
  
 `process`jest prawidłowy tylko podczas kompilowania za pomocą [/CLR](../build/reference/clr-common-language-runtime-compilation.md) lub **/CLR: pure** i nie jest prawidłowe podczas kompilowania za pomocą **/CLR: Safe**.  
  
 Każda domena aplikacji ma własną kopię zmiennej globalnej, należy użyć [elementu appdomain](../cpp/appdomain.md).  
  
 Zobacz [i domen aplikacji Visual C++](../dotnet/application-domains-and-visual-cpp.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [__declspec](../cpp/declspec.md)   
 [Słowa kluczowe](../cpp/keywords-cpp.md)