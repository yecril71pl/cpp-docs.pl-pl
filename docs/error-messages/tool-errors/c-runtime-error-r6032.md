---
title: Błąd czasu wykonania języka C R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: e0ae3acc491658840d74e262f3ab2719e613d60e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399996"
---
# <a name="c-runtime-error-r6032"></a>Błąd czasu wykonania języka C R6032

Brak wystarczającej ilości miejsca dla informacji o ustawieniach regionalnych

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez warunek bardzo małej ilości pamięci lub usterkę w programie.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Środowisko uruchomieniowe przechowuje informacje o ustawieniach regionalnych dla każdego wątku, tak, aby przetworzyć wywołania funkcji zależne od ustawień regionalnych. Jeśli alokacja pamięci dla tych informacji nie powiedzie się, środowisko uruchomieniowe nie może kontynuować, ponieważ zbyt wiele urządzeń podstawowych od niego zależne.