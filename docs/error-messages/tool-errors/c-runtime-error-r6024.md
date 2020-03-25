---
title: Błąd czasu wykonania języka C R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: de89d2e9e2b34f40b906a5dacca4179eade23f7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197200"
---
# <a name="c-runtime-error-r6024"></a>Błąd czasu wykonania języka C R6024

za mało miejsca na _onexit tabeli/atexit

> [!NOTE]
> Jeśli ten komunikat o błędzie wystąpi podczas uruchamiania aplikacji, aplikacja została zamknięta, ponieważ ma problem z pamięcią wewnętrzną. Ten błąd jest zwykle spowodowany przez bardzo małą ilość pamięci lub rzadko przez usterkę w programie lub uszkodzenie bibliotek wizualnych C++ , z których korzysta.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne uruchomione aplikacje lub Uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować program.
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować wszystkie kopie pakietu redystrybucyjnego C++ Microsoft Visual.
> - Sprawdź, **Windows Update** w **Panelu sterowania** aktualizacje oprogramowania.
> - Sprawdź dostępność zaktualizowanej wersji aplikacji. Jeśli problem będzie nadal występował, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, ponieważ nie ma dostępnej pamięci dla funkcji `_onexit` lub `atexit`. Ten błąd jest spowodowany przez warunek braku pamięci. Możesz rozważyć wstępne przydzielanie buforów podczas uruchamiania aplikacji, aby pomóc w zapisywaniu danych użytkownika i wykonywaniu czystego działania aplikacji w warunkach braku pamięci.
