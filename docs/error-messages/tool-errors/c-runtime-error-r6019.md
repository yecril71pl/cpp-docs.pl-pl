---
title: R6019 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6019
dev_langs:
- C++
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13653f54551501d5e35bd1285dc3d3f1a74343f1
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861606"
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