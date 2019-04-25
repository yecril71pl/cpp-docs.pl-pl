---
title: Błąd czasu wykonania języka C R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 5e1914d5d2f665609cfc24c2db3dc8a123d7e83f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299754"
---
# <a name="c-runtime-error-r6009"></a>Błąd czasu wykonania języka C R6009

Brak wystarczającej ilości miejsca dla środowiska

> [!NOTE]
> Jeśli napotkasz ten komunikat o błędzie podczas działania aplikacji, aplikacji został zamknięty, ponieważ ma on wewnętrzny problem z pamięcią. Istnieje kilka możliwych przyczyn tego błędu, ale często jest to spowodowane przez warunek bardzo małej ilości pamięci, zbyt dużej ilości pamięci, przez zmienne środowiskowe lub usterkę w programie.
>
> Możesz wypróbować następujące kroki, aby naprawić ten błąd:
>
> - Zamknij inne aplikacje uruchomione lub uruchom ponownie komputer, aby zwolnić pamięć.
> - Użyj **aplikacje i funkcje** lub **programy i funkcje** strony w **Panelu sterowania** naprawić lub zainstalować ponownie program.
> - Sprawdź **Windows Update** w **Panelu sterowania** aktualizacji oprogramowania.
> - Sprawdź, czy zaktualizowaną wersję aplikacji. Jeśli problem będzie się powtarzać, skontaktuj się z dostawcą aplikacji.

**Informacje dla programistów**

Było wystarczającej ilości pamięci, aby załadować program, ale nie ma wystarczającej ilości pamięci do utworzenia **envp** tablicy.  Może to być spowodowane przez warunki bardzo małej ilości pamięci lub przez użycie zmiennych środowiskowych nietypowo dużej. Należy wziąć pod uwagę jedną z następujących rozwiązań:

- Zwiększ ilość pamięci dostępnej dla programu.

- Zmniejsz liczbę i rozmiar argumentów wiersza polecenia.

- Zmniejsz rozmiar środowiska przez usunięcie niepotrzebnych zmiennych.