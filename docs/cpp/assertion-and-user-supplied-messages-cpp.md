---
title: Potwierdzanie i komunikaty dostarczone przez użytkownika (C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- user-supplied messages [C++], run time
- user-supplied messages [C++], preprocessor time
- '#error%2C assert%2C static_assert [C++]'
- user-supplied messages [C++], compile time
ms.assetid: ebf7d885-61c8-4233-b0ae-1c9a38e0f385
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e5f4a05c193ec471c0b8dd11d34961a46ead7660
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39406217"
---
# <a name="assertion-and-user-supplied-messages-c"></a>Potwierdzanie i komunikaty dostarczone przez użytkownika (C++)
C++ języka obsługuje trzy mechanizmy obsługi błędów, które ułatwiają debugowanie aplikacji: [dyrektywa #error](../preprocessor/hash-error-directive-c-cpp.md), [static_assert](../cpp/static-assert.md) — słowo kluczowe i [assert — makro, _assert, _ wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) makra. Wszystkie trzy mechanizmy emitują komunikaty o błędach a dwa testują również potwierdzenia oprogramowania. Potwierdzenie oprogramowania określa warunek, który będzie mieć wartość true w określonym punkcie w programie. Jeśli potwierdzenia w czasie kompilacji zakończą się niepowodzeniem, kompilator generuje komunikat diagnostyczny i błąd kompilacji. Jeśli potwierdzenia czasu wykonania nie powiodą się, system operacyjny wysyła komunikat diagnostyczny i zamyka aplikację.  
  
## <a name="remarks"></a>Uwagi  
 Okres istnienia aplikacji składa się z fazy przetwarzania wstępnego, fazy kompilacji i fazy czasu wykonywania. Każdy mechanizm obsługi błędów uzyskuje dostęp do informacji debugowania, które są dostępne podczas jednej z tych faz. Aby debugować skutecznie, wybierz ten mechanizm, który zapewnia odpowiednie informacje na temat tej fazy:  
  
-   [Dyrektywa #error](../preprocessor/hash-error-directive-c-cpp.md) jest aktywna w czasie przetwarzania wstępnego. Bezwarunkowo emituje komunikat określony przez użytkownika i powoduje niepowodzenie wskutek błędu kompilacji. Wiadomość może zawierać tekst, który jest przetwarzany przez dyrektywy preprocesora, ale żadne wyrażenie warunkowe nie zostaje ocenione.  
  
-   [Static_assert](../cpp/static-assert.md) deklaracji jest aktywna w czasie kompilacji. Sprawdza potwierdzenia oprogramowania, które są reprezentowane przez wyrażenia integralne określone przez użytkownika, które można przekonwertować na wartość logiczną. Jeśli wyrażenie ma wartość zero (false), kompilator generuje komunikat określony przez użytkownika i kompilacja nie powiedzie się z powodu błędu.  
  
     Deklaracja `static_assert` jest szczególnie przydatna podczas debugowania szablonów, ponieważ argumenty szablonu mogą być zawarte w wyrażeniu określonym przez użytkownika.  
  
-   [Assert — makro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md) — makro jest aktywna w czasie wykonywania. Ocenia wyrażenia określone przez użytkownika, a jeśli wynik wynosi zero, system wysyła komunikat diagnostyczny i zamyka aplikację. Wiele innych makr, takich jak[_ASSERT](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) i _asserte —, przypominają to makro, ale emitują różne komunikaty diagnostyczne zdefiniowane przez system lub zdefiniowanych przez użytkownika.  
  
## <a name="see-also"></a>Zobacz także  
 [#error — dyrektywa (C/C++)](../preprocessor/hash-error-directive-c-cpp.md)   
 [assert Macro, _assert, _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)   
 [_ASSERT, _asserte —, _ASSERT_EXPR makra](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)   
 [static_assert](../cpp/static-assert.md)   
 [_STATIC_ASSERT — makro](../c-runtime-library/reference/static-assert-macro.md)   
 [Szablony](../cpp/templates-cpp.md)