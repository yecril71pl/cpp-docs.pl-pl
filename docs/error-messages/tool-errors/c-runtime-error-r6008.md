---
title: R6008 błąd środowiska uruchomieniowego języka C | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- R6008
dev_langs:
- C++
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 39b06566f84003b08f5fe3869a021c4bf86dcf5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105152"
---
# <a name="c-runtime-error-r6008"></a>R6008 błąd środowiska uruchomieniowego języka C

Brak wystarczającej ilości miejsca dla argumentów

> [!NOTE]
>  Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez warunek bardzo małej ilości pamięci, zbyt dużej ilości pamięci, przez zmienne środowiskowe lub usterkę w programie.
>
>  Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
>  -   Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> -   Zmniejsz liczbę i rozmiar argumentów wiersza polecenia do aplikacji.
> -   Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> -   Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> -   Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Było wystarczającej ilości pamięci, aby załadować program, ale nie ma wystarczającej ilości pamięci do utworzenia **argv** tablicy. Może to być spowodowane przez warunki bardzo małej ilości pamięci lub przez nietypowo dużej wierszy polecenia lub użycia zmiennych środowiskowych. Należy wziąć pod uwagę jedną z następujących rozwiązań:

- Zwiększ ilość pamięci dostępnej dla programu.

- Zmniejsz liczbę i rozmiar argumentów wiersza polecenia.

- Zmniejsz rozmiar środowiska przez usunięcie niepotrzebnych zmiennych.