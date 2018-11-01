---
title: R6027 błąd środowiska uruchomieniowego języka C
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 2884f148091d9407d3229f0690a161639b5195e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50446518"
---
# <a name="c-runtime-error-r6027"></a>R6027 błąd środowiska uruchomieniowego języka C

Brak wystarczającej ilości miejsca do zainicjowania lowio

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje kilka możliwych przyczyn tego błędu, ale zazwyczaj jest to spowodowane przez warunek bardzo małej ilości pamięci. Może być także spowodowane przez usterkę w aplikacji, uszkodzenie bibliotek Visual C++, których używa lub sterownika.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Jeśli aplikacja była praca przed Ostatnia instalacja innej aplikacji lub sterownika, użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** do usunięcia Nowa aplikacja lub sterownika i spróbuj ponownie aplikację.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie wszystkie kopie Microsoft Visual C++ Redistributable.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Ten błąd występuje, gdy nie ma wystarczającej ilości wolnego pamięci zainicjować obsługi operacji We/Wy niskiego poziomu, w środowisku uruchomieniowym języka C. Ten błąd zazwyczaj występuje podczas uruchamiania aplikacji. Upewnij się, że Twoja aplikacja i sterowniki i bibliotek DLL, która ładuje nie spowodują uszkodzenia sterty przy uruchamianiu.