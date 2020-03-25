---
title: Błąd czasu wykonania języka C R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b29b946d08cff903cf0ca398ba0d7589cb5d54ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197096"
---
# <a name="c-runtime-error-r6032"></a>Błąd czasu wykonania języka C R6032

Za mało miejsca na informacje o ustawieniach regionalnych

> [!NOTE]
> Jeśli ten komunikat o błędzie wystąpi podczas uruchamiania aplikacji, aplikacja została zamknięta, ponieważ ma problem z pamięcią wewnętrzną. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane bardzo małą ilością pamięci lub usterką w programie.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne uruchomione aplikacje lub Uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj strony **aplikacje i funkcje** lub **programy i funkcje** w **Panelu sterowania** , aby naprawić lub ponownie zainstalować program.
> - Sprawdź, **Windows Update** w **Panelu sterowania** aktualizacje oprogramowania.
> - Sprawdź dostępność zaktualizowanej wersji aplikacji. Jeśli problem będzie nadal występował, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Środowisko uruchomieniowe utrzymuje informacje o ustawieniach regionalnych poszczególnych wątków, aby można było przetwarzać wywołania do funkcji zależnych od ustawień regionalnych. Jeśli alokacja pamięci dla tych informacji nie powiedzie się, środowisko uruchomieniowe nie może działać, ponieważ zależą od niej zbyt wiele podstawowych funkcji.
