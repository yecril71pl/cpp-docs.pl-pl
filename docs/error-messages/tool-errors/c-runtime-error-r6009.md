---
title: Błąd czasu wykonania języka C R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 64391f8ec05a99bb85a9d6cd00d6488a945fdb62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197356"
---
# <a name="c-runtime-error-r6009"></a>Błąd czasu wykonania języka C R6009

za mało miejsca na środowisko

> [!NOTE]
> Jeśli ten komunikat o błędzie wystąpi podczas uruchamiania aplikacji, aplikacja została zamknięta, ponieważ ma problem z pamięcią wewnętrzną. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane bardzo małą ilością pamięci, zbyt dużą ilością pamięci przez zmienne środowiskowe lub usterką w programie.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne uruchomione aplikacje lub Uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować program.
> - Sprawdź, **Windows Update** w **Panelu sterowania** aktualizacje oprogramowania.
> - Sprawdź dostępność zaktualizowanej wersji aplikacji. Jeśli problem będzie nadal występował, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Za mało pamięci, aby załadować program, ale za mało pamięci, aby utworzyć tablicę **envp** .  Przyczyną może być bardzo mała ilość pamięci lub niezazwyczaj duże użycie zmiennej środowiskowej. Rozważ jedno z następujących rozwiązań:

- Zwiększ ilość pamięci dostępnej dla programu.

- Zmniejsz liczbę i rozmiar argumentów wiersza polecenia.

- Zmniejsz rozmiar środowiska, usuwając zbędne zmienne.
