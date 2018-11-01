---
title: R6024 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: 89b99a93512603eaf2273a6ff3f434f1ad3b3bb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497073"
---
# <a name="c-runtime-error-r6024"></a>R6024 błąd środowiska uruchomieniowego języka C

Brak wystarczającej ilości miejsca dla tabeli _onexit/atexit

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Ten błąd jest zazwyczaj powodowane przez warunek bardzo małej ilości pamięci lub rzadko, usterki w programie lub uszkodzenie bibliotek Visual C++, których używa.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie wszystkie kopie Microsoft Visual C++ Redistributable.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, ponieważ pamięć nie jest dostępna dla `_onexit` lub `atexit` funkcji. Ten błąd jest spowodowany przez niedostatecznej ilości pamięci. Należy rozważyć, wstępnie przydziela buforów przy uruchamianiu aplikacji, aby pomóc w zapisując dane i wykonywanie czystej aplikacji Zamknij warunków małej ilości pamięci.