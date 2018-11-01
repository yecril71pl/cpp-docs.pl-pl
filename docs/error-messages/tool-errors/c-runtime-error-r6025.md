---
title: R6025 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 461bfb2aa46053ec56fff67de70038b1fcd97389
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639571"
---
# <a name="c-runtime-error-r6025"></a>R6025 błąd środowiska uruchomieniowego języka C

Wywołanie czystych funkcji wirtualnych

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem. Najbardziej typową przyczyną tego błędu jest to błąd w aplikacji lub uszkodzenie instalacji.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Żaden obiekt nie został uruchomiony obsłużyć wywołania czystą funkcję wirtualną.

Ten błąd jest spowodowany przez wywołanie funkcji wirtualnej w abstrakcyjna klasa bazowa, za pomocą wskaźnika, który jest tworzony przez rzutowanie na typ klasy pochodnej, ale jest właściwie wskaźnikiem do klasy bazowej. Taka sytuacja może wystąpić, gdy rzutowanie z **void** <strong>\*</strong> na wskaźnik do klasy podczas **void** <strong>\*</strong> został tworzone podczas tworzenia klasy bazowej.

