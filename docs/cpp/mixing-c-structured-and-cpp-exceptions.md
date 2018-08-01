---
title: Połączenie wyjątków języka C++ i C (strukturalnych) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exceptions [C++], mixed C and C++
- C++ exception handling, mixed-language
- structured exception handling [C++], mixed C and C++
- catch keyword [C++], mixed
- try-catch keyword [C++], mixed-language
ms.assetid: a149154e-36dd-4d1a-980b-efde2a563a56
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6e632faddb3b4f59733710a915ed121a12f4e0c6
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404866"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Połączenie wyjątków języka C (strukturalnych) i C++
Aby napisać bardziej przenośny kod, nie jest zalecane wykorzystanie strukturalnej obsługi wyjątków w programie w języku C++. Jednak czasami warto skompilować z **/eha** i wymieszać strukturalne wyjątki kodu źródłowego języka C++, a zatem potrzebne są funkcje obsługi obu rodzajów wyjątków. Ponieważ program obsługi wyjątków strukturalnych nie ma koncepcji obiektów lub wyjątków z określonym typem, nie może obsługiwać wyjątki generowane przez kod języka C++; jednak C++ **catch** obsługi mogą obsługiwać wyjątki strukturalne. Jako taka, składnia obsługi wyjątków C++ (**spróbuj**, **throw**, **catch**) nie jest akceptowana przez kompilator C, natomiast składnia obsługi wyjątków strukturalnych (**__try** , **__except**, **__finally**) jest obsługiwana przez kompilator języka C++.  
  
 Zobacz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) uzyskać informacji na temat obsługi wyjątków strukturalnych jako wyjątków C++.  
  
 Po przemieszaniu wyjątków strukturalnych z wyjątkami C++, należy pamiętać o następujących kwestiach:  
  
1.  Wyjątki C++ i wyjątki strukturalne nie mogą być mieszane w obrębie tej samej funkcji.  
  
2.  Programy obsługi zakończenia (**__finally** bloków) są wykonywane zawsze, nawet w trakcie rozwijania po zgłaszany jest wyjątek.  
  
3.  Obsługa wyjątków języka C++ może wychwycić i zachować semantykę operacji unwind we wszystkich modułach skompilowanych z [/EH](../build/reference/eh-exception-handling-model.md) — opcja kompilatora (opcja ta włącza semantykę rozwijania).  
  
4.  Istnieją sytuacje, w których funkcje destruktora nie są wywoływane dla wszystkich obiektów. Na przykład, jeśli wyjątek strukturalny występuje podczas próby wywołania funkcji przez niezainicjowany wskaźnik funkcji i funkcja ta przyjmuje jako parametry obiekty, które zostały zbudowane przed wywołaniem, destruktory tych obiektów nie będą wywoływane podczas odwijania stosu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat?  
  
-   [Wykorzystanie setjmp lub longjmp w programach języka C++](../cpp/using-setjmp-longjmp.md)  
  
-   [Różnice między SEH i EH w języku C++](../cpp/exception-handling-differences.md)  
  
## <a name="see-also"></a>Zobacz także  
 [Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)