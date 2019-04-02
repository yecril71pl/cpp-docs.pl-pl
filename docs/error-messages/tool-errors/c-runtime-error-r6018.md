---
title: R6018 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: b36e2184e5be131645fb4dd58a361fdb9a31da63
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774980"
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

Aby rozwiązać ten problem, sprawdź, czy błędy uszkodzenia sterty w kodzie. Aby uzyskać więcej informacji i przykładów, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Następnie sprawdź, czy są przy użyciu najnowszych pakietów redystrybucyjnych dla danego wdrożenia aplikacji. Aby uzyskać informacje, zobacz [wdrożenia w programie Visual C++](../../windows/deployment-in-visual-cpp.md).