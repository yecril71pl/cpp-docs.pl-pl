---
title: Błąd czasu wykonania języka C R6002
ms.date: 11/04/2016
f1_keywords:
- R6002
helpviewer_keywords:
- R6002
ms.assetid: 8fbbe65a-9c43-459e-8342-e1f6d1cef7d0
ms.openlocfilehash: f8b5fe69c9fd688f4d0a181176cda247cde9ac11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380542"
---
# <a name="c-runtime-error-r6002"></a>Błąd czasu wykonania języka C R6002

Obsługa liczb zmiennoprzecinkowych nie załadowano

Niezbędne biblioteki zmiennoprzecinkowe nie został połączony.

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez wadę w kodzie aplikacji lub przy próbie uruchomienia aplikacji, która nie została skompilowana dla procesora konkretnego komputera.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd może wystąpić w swojej aplikacji, gdy biblioteka zmiennoprzecinkowe nie został połączony. Sprawdź, czy jeden z tych przyczyn:

- Ciąg formatu dla `printf_s` lub `scanf_s` funkcja zawarte specyfikacji formatu zmiennoprzecinkowego i program nie zawiera żadnych wartości zmiennoprzecinkowych lub zmienne. Aby rozwiązać ten problem, użyj argumentu zmiennoprzecinkowego, aby odpowiadać specyfikacji formatu zmiennoprzecinkowego lub wykonać zmiennoprzecinkowych przypisania w innym miejscu w programie. To powoduje, że obsługa modelu zmiennoprzecinkowego do załadowania.

- Kompilator minimalizuje rozmiar programu, ładując Obsługa liczb zmiennoprzecinkowych tylko wtedy, gdy jest to konieczne. Kompilator nie może wykryć operacji zmiennoprzecinkowych lub specyfikacji formatu zmiennoprzecinkowego ciągów formatu, dzięki czemu nie ładuje niezbędnych procedur zmiennoprzecinkowych. Aby rozwiązać ten problem, użyj specyfikacji formatu zmiennoprzecinkowego i podać argument zmiennoprzecinkowy lub wykonać zmiennoprzecinkowych przypisania w innym miejscu w programie. To powoduje, że obsługa modelu zmiennoprzecinkowego do załadowania.

- W programie w językach mieszanych biblioteki C została określona przed biblioteki FORTRAN, gdy program został połączony. Połącz ponownie, a ostatnia określ bibliotekę języka C.