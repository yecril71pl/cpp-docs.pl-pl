---
title: "Połączenie wyjątków języka C++ i C (strukturalnych) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 375f954f3df300b50a11067b009614ff8879b9b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Połączenie wyjątków języka C (strukturalnych) i C++
Aby napisać bardziej przenośny kod, nie jest zalecane wykorzystanie strukturalnej obsługi wyjątków w programie w języku C++. Jednak czasami można skompilować z **/eha** mieszać wyjątki strukturalne i kod źródłowy C++ i wymagają niektóre funkcje obsługi obu rodzajów wyjątków. Ponieważ program obsługi wyjątków strukturalnych nie ma żadnych koncepcji obiektów lub typu wyjątki, nie może obsługiwać wyjątków zgłaszanych przez kod C++; jednak C++ **catch** programy obsługi można Obsługa wyjątków strukturalnych. Jako takie, Obsługa składni wyjątków języka C++ (**spróbuj**, `throw`, **catch**) nie jest akceptowane przez kompilator języka C, ale składni obsługi wyjątków strukturalnych (`__try`, `__except`, `__finally`) jest obsługiwana przez kompilator języka C++.  
  
 Zobacz [_set_se_translator —](../c-runtime-library/reference/set-se-translator.md) informacji dotyczących obsługi wyjątków strukturalnych wyjątków C++.  
  
 Po przemieszaniu wyjątków strukturalnych z wyjątkami C++, należy pamiętać o następujących kwestiach:  
  
1.  Wyjątki C++ i wyjątki strukturalne nie mogą być mieszane w obrębie tej samej funkcji.  
  
2.  Programy obsługi zakończenia (bloki `__finally`) są wykonywane zawsze, nawet w trakcie rozwijania po zgłoszeniu wyjątku.  
  
3.  Można przechwycić C++, obsługa wyjątków i Zachowaj unwind semantyki we wszystkich modułach skompilowane z [/EH](../build/reference/eh-exception-handling-model.md) — opcja kompilatora (Ta opcja umożliwia semantyką rozwinięć).  
  
4.  Istnieją sytuacje, w których funkcje destruktora nie są wywoływane dla wszystkich obiektów. Na przykład, jeśli wyjątek strukturalny występuje podczas próby wywołania funkcji przez niezainicjowany wskaźnik funkcji i funkcja ta przyjmuje jako parametry obiekty, które zostały zbudowane przed wywołaniem, destruktory tych obiektów nie będą wywoływane podczas odwijania stosu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
  
-   [Przy użyciu setjmp / longjmp w programach języka C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Różnice między SEH i C++ EH](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)