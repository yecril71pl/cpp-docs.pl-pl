---
title: R6019 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: 93d340b2a12a00420a9003429251387b2f04ad37
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548073"
---
# <a name="c-runtime-error-r6019"></a>R6019 błąd środowiska uruchomieniowego języka C

Nie można otworzyć konsoli urządzenia

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ próbowała ona dostęp do konsoli, ale go nie ma wystarczających uprawnień. Istnieje kilka możliwych przyczyn tego błędu, ale zwykle jest to spowodowane należy uruchomić program jako administrator lub jest to błąd w programie.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Uruchom program jako administrator.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, ponieważ aplikacja wywołuje funkcję konsoli, ale system operacyjny nie udostępni dostęp do konsoli. Z wyjątkiem w trybie debugowania, konsoli funkcje zwykle nie są dozwolone w aplikacji Microsoft Store. Jeśli aplikacja wymaga uprawnień administratora do uruchomienia, upewnij się, że jest zainstalowana do uruchamiania jako administrator, domyślnie.