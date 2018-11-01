---
title: R6018 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: e0d229b4fd8c1a4f8e067c0e59a278344fd4e113
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531921"
---
# <a name="c-runtime-error-r6018"></a>R6018 błąd środowiska uruchomieniowego języka C

Błąd nieoczekiwanego sterty

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez wadę w kodzie aplikacji.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Program napotkał nieoczekiwany błąd podczas wykonywania operacji zarządzania pamięcią.

Ten błąd występuje przeważnie, jeśli program zmienia przypadkowo danych sterty środowiska wykonawczego. Jednak go może również być spowodowany przez błąd wewnętrzny w czasie wykonywania lub kodu systemu operacyjnego.

Aby rozwiązać ten problem, sprawdź, czy błędy uszkodzenia sterty w kodzie. Aby uzyskać więcej informacji i przykładów, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Następnie sprawdź, czy są przy użyciu najnowszych pakietów redystrybucyjnych dla danego wdrożenia aplikacji. Aby uzyskać informacje, zobacz [wdrożenia w programie Visual C++](../../ide/deployment-in-visual-cpp.md).