---
title: R6032 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6032
dev_langs:
- C++
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43155f24411fb5206a03d607f0551c2d34294aeb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024206"
---
# <a name="c-runtime-error-r6032"></a>R6032 błąd środowiska uruchomieniowego języka C

Brak wystarczającej ilości miejsca dla informacji o ustawieniach regionalnych

> [!NOTE]
>  Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez warunek bardzo małej ilości pamięci lub usterkę w programie.
>
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
>  -   Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> -   Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Środowisko uruchomieniowe przechowuje informacje o ustawieniach regionalnych dla każdego wątku, tak, aby przetworzyć wywołania funkcji zależne od ustawień regionalnych. Jeśli alokacja pamięci dla tych informacji nie powiedzie się, środowisko uruchomieniowe nie może kontynuować, ponieważ zbyt wiele urządzeń podstawowych od niego zależne.