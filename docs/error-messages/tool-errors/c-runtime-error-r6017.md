---
title: R6017 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6017
dev_langs:
- C++
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: acd380c8eee7b4fa1b325e8dee0bfad55a42c790
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861073"
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

Aby rozwiązać ten problem, sprawdź, czy błędy uszkodzenia sterty w kodzie. Aby uzyskać więcej informacji i przykładów, zobacz [szczegóły dotyczące sterty debugowania CRT](/visualstudio/debugger/crt-debug-heap-details). Następnie sprawdź, czy są przy użyciu najnowszych pakietów redystrybucyjnych dla danego wdrożenia aplikacji. Aby uzyskać informacje, zobacz [wdrożenia w programie Visual C++](../../ide/deployment-in-visual-cpp.md).