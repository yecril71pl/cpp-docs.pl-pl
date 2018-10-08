---
title: R6028 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6028
dev_langs:
- C++
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dbcc1f34fced7a7ea752d8733662f7510a01aad5
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48860553"
---
# <a name="c-runtime-error-r6028"></a>R6028 błąd środowiska uruchomieniowego języka C

nie można zainicjować sterty

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje wiele możliwych przyczyn tego błędu, ale często jest to spowodowane przez warunek bardzo małej ilości pamięci, usterki w programie lub uszkodzenie sprzętu sterowników.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Jeśli aplikacja była praca przed Ostatnia instalacja innej aplikacji lub sterownika, użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** do usunięcia Nowa aplikacja lub sterownika i spróbuj ponownie aplikację.
> - Sprawdź witrynę sieci Web z dostawcą sprzętu lub **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania i sterowników.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, gdy system operacyjny nie może utworzyć puli pamięci dla aplikacji. W szczególności C Runtime (CRT) wywołała funkcję Win32 `HeapCreate`, która zwróciła wartość NULL wskazującą niepowodzenie.

Jeśli ten błąd występuje podczas uruchamiania aplikacji, system może nie być w stanie spełnić żądań sterty, ponieważ ładowane są uszkodzone sterowniki. Sprawdź witrynę Windows Update lub witrynę dostawcy sprzętu, aby uzyskać zaktualizowane sterowniki.