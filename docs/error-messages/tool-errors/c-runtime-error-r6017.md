---
title: R6017 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 45f3b07f540cb72a955b19420130a5a806b750d7
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58774701"
---
# <a name="c-runtime-error-r6017"></a>R6017 błąd środowiska uruchomieniowego języka C

Błąd nieoczekiwanego blokady wielowątkowych

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez wadę w kodzie aplikacji.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Proces Odebrano nieoczekiwany błąd podczas próby uzyskania dostępu do języka C środowiska uruchomieniowego wielowątkowych blokady dla zasobu systemowego. Ten błąd występuje przeważnie, jeśli proces przypadkowo zmienia dane sterty środowiska uruchomieniowego. Jednak to może również być spowodowane błąd wewnętrzny w bibliotece wykonawczej lub kodu systemu operacyjnego.

Aby rozwiązać ten problem, sprawdź, czy błędy uszkodzenia sterty w kodzie. Aby uzyskać więcej informacji i przykładów, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Następnie sprawdź, czy są przy użyciu najnowszych pakietów redystrybucyjnych dla danego wdrożenia aplikacji. Aby uzyskać informacje, zobacz [wdrożenia w programie Visual C++](../../windows/deployment-in-visual-cpp.md).