---
title: R6016 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: b617e3cf6d48a24b01479ef7ef3fb6ac425b3996
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556952"
---
# <a name="c-runtime-error-r6016"></a>R6016 błąd środowiska uruchomieniowego języka C

za mało miejsca dla danych wątku

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje wiele możliwych przyczyn tego błędu, ale często jest to spowodowane przez warunek bardzo małej ilości pamięci usterkę w aplikacji lub usterkę w dodatku lub rozszerzenie używane przez aplikację.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie aplikację.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** usunąć, naprawy lub ponownej instalacji dodatków lub rozszerzeń używanych przez aplikację.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, ponieważ program nie otrzymał od systemu operacyjnego, aby ukończyć wystarczającej ilości pamięci [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) lub `_beginthreadex` wywołania lub lokalny magazyn nie został zainicjowany przez wątek `_beginthread` lub `_beginthreadex`.

W momencie rozpoczynania nowego wątku biblioteka musi utworzyć wewnętrzną bazę danych dla tego wątku. Jeśli baza danych nie może zostać rozszerzona przy użyciu pamięci dostarczonej przez system operacyjny, wątek się nie rozpoczyna, a proces wywołujący się zatrzymuje. Może się to zdarzyć, gdy proces utworzył zbyt wiele wątków lub gdy pamięć lokalna wątku została wyczerpana.

Zaleca się, że plik wykonywalny, który wywołuje biblioteki środowiska uruchomieniowego języka C (CRT) powinny używać `_beginthreadex` tworzenia wątku, a nie interfejsu Windows API `CreateThread`. `_beginthreadex` Inicjuje wewnętrzną pamięć statyczną, używane przez wiele funkcji CRT w pamięci lokalnej wątku. Jeśli używasz `CreateThread` Aby utworzyć wątek, CRT może zakończyć proces z R6016, gdy następuje wywołanie funkcji CRT, która wymaga zainicjowanej wewnętrznej pamięci statycznej.