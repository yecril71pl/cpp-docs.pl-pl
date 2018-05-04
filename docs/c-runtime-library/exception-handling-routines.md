---
title: Obsługa wyjątków — procedury | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.exceptions
dev_langs:
- C++
helpviewer_keywords:
- exception handling, routines
ms.assetid: f60548c6-850a-4e1e-a79b-a2a6a541ab62
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eea92c5bfdb54b6c15ae2ae643b2d23b397a3bf6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="exception-handling-routines"></a>Obsługa wyjątków — Procedury

Do odzyskania z nieoczekiwanych zdarzeń podczas wykonywania programu, należy użyć funkcji obsługi wyjątków języka C++.

## <a name="exception-handling-functions"></a>Funkcje obsługi wyjątków

|Funkcja|Zastosowanie|
|--------------|---------|
|[_set_se_translator](../c-runtime-library/reference/set-se-translator.md)|Uchwyt Win32 wyjątków (C strukturalnych wyjątkami), ponieważ C++ wpisane wyjątków|
|[set_terminate —](../c-runtime-library/reference/set-terminate-crt.md)|Zainstaluj własne procedury zakończenia ma zostać wywołana przez **przerwanie**|
|[set_unexpected](../c-runtime-library/reference/set-unexpected-crt.md)|Zainstaluj własnej funkcji zakończenia ma zostać wywołana przez **nieoczekiwany**|
|[Zakończenie](../c-runtime-library/reference/terminate-crt.md)|Wywołuje się automatycznie w pewnych okolicznościach po wyjątku. **Przerwanie** wywołania funkcji **przerwać** lub funkcję należy ją określić za pomocą **set_terminate —**|
|[Nieoczekiwany](../c-runtime-library/reference/unexpected-crt.md)|Wywołania **przerwanie** lub funkcję należy ją określić za pomocą **set_unexpected —**. **Nieoczekiwany** funkcja nie jest używana w bieżącej implementacji obsługi wyjątków C++ firmy Microsoft|

## <a name="see-also"></a>Zobacz też

[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
