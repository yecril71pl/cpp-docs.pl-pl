---
title: Mieszanie C (ze strukturą) i wyjątki języka C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/14/2018
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
ms.openlocfilehash: 1edd35ac9f32a28a19c4ea54b7e9fba2820d6095
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031629"
---
# <a name="mixing-c-structured-and-c-exceptions"></a>Mieszanie C (ze strukturą) i wyjątki języka C++

Korzystanie ze strukturą obsługi wyjątków (SEH) w programie C++ nie jest zalecane, jeśli chcesz tworzyć przenośny kod. Jednak czasami warto skompilować przy użyciu [/eha](../build/reference/eh-exception-handling-model.md) i wymieszać strukturalne wyjątki kodu źródłowego języka C++, a zatem potrzebne są funkcje obsługi obu rodzajów wyjątków. Ponieważ program obsługi wyjątków strukturalnych nie ma koncepcji obiektów lub wyjątków z określonym typem, nie może obsługiwać wyjątki generowane przez kod języka C++. Jednak C++ **catch** obsługi mogą obsługiwać wyjątki strukturalne. Składnia obsługi wyjątków C++ (**spróbuj**, **throw**, **catch**) nie jest akceptowana przez kompilator C, natomiast składnia obsługi wyjątków strukturalnych (**__try**, **__except**, **__finally**) jest obsługiwana przez kompilator języka C++.

Zobacz [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) informacji na temat obsługi wyjątków strukturalnych jako wyjątków C++.

Po przemieszaniu ze strukturą i wyjątków języka C++, należy pamiętać o tych potencjalnych problemów:

- Wyjątki C++ i wyjątki strukturalne nie mogą być mieszane w obrębie tej samej funkcji.

- Programy obsługi zakończenia (**__finally** bloków) są wykonywane zawsze, nawet w trakcie rozwijania po zgłaszany jest wyjątek.

- Obsługa wyjątków języka C++ może wychwycić i zachować semantykę operacji unwind we wszystkich modułach skompilowanych z [/EH](../build/reference/eh-exception-handling-model.md) opcje kompilatora, które umożliwiają semantykę operacji unwind.

- Istnieją sytuacje, w których funkcje destruktora nie są wywoływane dla wszystkich obiektów. Na przykład jeśli wyjątek strukturalny występuje podczas próby wywołania funkcji przez niezainicjowany wskaźnik funkcji, a funkcja ta przyjmuje jako parametry obiekty, które zostały zbudowane przed wywołaniem, destruktory tych obiektów nie są wywoływane Podczas odwijania stosu.

## <a name="next-steps"></a>Następne kroki

- [Wykorzystanie setjmp lub longjmp w programach języka C++](../cpp/using-setjmp-longjmp.md)

  Zobacz więcej informacji dotyczących stosowania `setjmp` i `longjmp` w programach języka C++.

- [Obsługa wyjątków strukturalnych w języku C++](../cpp/exception-handling-differences.md)

  Zobacz przykłady sposobów C++ można użyć do uchwytu, ze strukturą wyjątków.

## <a name="see-also"></a>Zobacz także

[Obsługa wyjątków języka C++](../cpp/cpp-exception-handling.md)
