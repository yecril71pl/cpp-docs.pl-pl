---
title: Błąd czasu wykonania języka C R6026
ms.date: 11/04/2016
f1_keywords:
- R6026
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
ms.openlocfilehash: c0f2f6371933d118bf52328726fb2c68907c2666
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197187"
---
# <a name="c-runtime-error-r6026"></a>Błąd czasu wykonania języka C R6026

za mało miejsca na zainicjowanie stdio

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

Ten błąd występuje w przypadku braku wystarczającej ilości wolnej pamięci umożliwiającej zainicjowanie obsługi standardowej operacji we/wy w środowisku uruchomieniowym języka C. Ten błąd występuje zwykle podczas uruchamiania aplikacji. Sprawdź, czy aplikacja oraz sterowniki i biblioteki DLL, które ładuje, nie uszkadzają sterty podczas uruchamiania.
