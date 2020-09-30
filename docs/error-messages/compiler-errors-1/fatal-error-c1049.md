---
title: Błąd krytyczny C1049
description: Opis błędu krytycznego kompilatora C1049, nieprawidłowy argument liczbowy i wyjaśniono, jak go rozwiązać.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: 9b3cbe5d081e32680e5408fc4a6ddcd932db77a2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503275"
---
# <a name="fatal-error-c1049"></a>Błąd krytyczny C1049

> Nieprawidłowy liczbowy argument "*Value*"

Analizator wiersza polecenia CL.EXE znalazł *wartość* , w której Oczekiwano argumentu numerycznego.

Błąd C1049 może wystąpić, gdy kompilator nie może znaleźć argumentu liczbowego dla jednej z następujących opcji kompilatora:

[/constexpr: Głębokość](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr: śledzenie](../../build/reference/constexpr-control-constexpr-evaluation.md)\
[/constexpr: kroki](../../build/reference/constexpr-control-constexpr-evaluation.md)

Opcje kompilatora wiersza polecenia, które oczekują argumentu liczbowego, mogą również raportować `Command line error D8004` , `Command line error D8021` ,, `Command line warning D9002` `Command line warning D9014` lub `Command line warning D9024` .

Aby rozwiązać ten problem, przejrzyj wiersz polecenia pod kątem nieumieszczonych lub brakujących argumentów. Sprawdź, czy nie ma nieoczekiwanego odstępu między opcjami i argumentami. Ostatni wiersz polecenia może być generowany przez makra, zmienne środowiskowe lub inne operacje kompilacji systemu. Dlatego ważne jest, aby sprawdzić, czy rzeczywisty wiersz polecenia przeszedł do kompilatora.

- W plikach poleceń lub pliku reguł programu make można użyć polecenia **echo** , aby zgłosić rzeczywisty wiersz polecenia.

- W programie Visual Studio Otwórz okno dialogowe **strony właściwości** projektu. Na stronie **Ogólne właściwości konfiguracji**  >  **C/C++**  >  **General** Zmień właściwość **pomijanie transparentu startowego** na wartość **nie**. Wybierz **przycisk OK** , aby zapisać zmiany. Okno **dane wyjściowe** wyświetla teraz wiersz polecenia podczas kompilowania, bezpośrednio po wierszu praw autorskich.

Inne systemy kompilacji mogą mieć pliki dziennika lub pełne opcje, aby zobaczyć rzeczywiste polecenia. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją systemu kompilacji.
