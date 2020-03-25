---
title: Błąd czasu wykonania języka C R6027
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 8c2aab7b090dbfa4553b8d1622f13aef13f58aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197174"
---
# <a name="c-runtime-error-r6027"></a>Błąd czasu wykonania języka C R6027

za mało miejsca na zainicjowanie lowio

> [!NOTE]
> Jeśli ten komunikat o błędzie wystąpi podczas uruchamiania aplikacji, aplikacja została zamknięta, ponieważ ma problem z pamięcią wewnętrzną. Istnieje kilka możliwych przyczyn tego błędu, ale zazwyczaj jest to spowodowane bardzo małą ilością pamięci. Może być również przyczyną błędu w aplikacji przez uszkodzenie bibliotek wizualnych C++ , których używa, lub przez sterownik.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne uruchomione aplikacje lub Uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować program.
> - Jeśli aplikacja działała przed ostatnią instalacją innej aplikacji lub sterownika, użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby usunąć nową aplikację lub sterownik, a następnie spróbuj ponownie wykonać swoją aplikację.
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować wszystkie kopie pakietu redystrybucyjnego C++ Microsoft Visual.
> - Sprawdź, **Windows Update** w **Panelu sterowania** aktualizacje oprogramowania.
> - Sprawdź dostępność zaktualizowanej wersji aplikacji. Jeśli problem będzie nadal występował, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, gdy jest za mało dostępnej wolnej pamięci, aby zainicjować obsługę operacji we/wy niskiego poziomu w środowisku uruchomieniowym języka C. Ten błąd występuje zwykle podczas uruchamiania aplikacji. Sprawdź, czy aplikacja oraz sterowniki i biblioteki DLL, które ładuje, nie uszkadzają sterty podczas uruchamiania.
