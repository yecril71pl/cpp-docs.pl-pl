---
title: Błąd krytyczny C1049
description: Opis błędu krytycznego kompilatora C1049, nieprawidłowy argument liczbowy i wyjaśniono, jak go rozwiązać.
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: f2669eec4bafb24f26c405d4fa74a96fe5337d13
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633197"
---
# <a name="fatal-error-c1049"></a>Błąd krytyczny C1049

> Nieprawidłowy liczbowy argument "*Value*"

CL. Analizator wiersza polecenia EXE znalazł *wartość* , w której Oczekiwano argumentu numerycznego.

Błąd C1049 może wystąpić, gdy kompilator nie może znaleźć argumentu liczbowego dla jednej z następujących opcji kompilatora:

[/constexpr: głębokość](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr: śledzenie nieprześledzone](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr: kroki](/cpp/build/reference/constexpr-control-constexpr-evaluation)

Opcje kompilatora wiersza polecenia, które oczekują argumentu numerycznego, mogą również raportować `Command line error D8004`, `Command line error D8021`, `Command line warning D9002`, `Command line warning D9014`lub `Command line warning D9024`.

Aby rozwiązać ten problem, przejrzyj wiersz polecenia pod kątem nieumieszczonych lub brakujących argumentów. Sprawdź, czy nie ma nieoczekiwanego odstępu między opcjami i argumentami. Ostatni wiersz polecenia może być generowany przez makra, zmienne środowiskowe lub inne operacje kompilacji systemu. Dlatego ważne jest, aby sprawdzić, czy rzeczywisty wiersz polecenia przeszedł do kompilatora.

- W plikach poleceń lub pliku reguł programu make można użyć polecenia **echo** , aby zgłosić rzeczywisty wiersz polecenia.

- W programie Visual Studio Otwórz okno dialogowe **strony właściwości** projektu. Na stronie **Ogólne** **Właściwości konfiguracji** > **CC++ /**  > Zmień właściwość **pomijanie transparentu startowego** na wartość **nie**. Wybierz **przycisk OK** , aby zapisać zmiany. Okno **dane wyjściowe** wyświetla teraz wiersz polecenia podczas kompilowania, bezpośrednio po wierszu praw autorskich.

Inne systemy kompilacji mogą mieć pliki dziennika lub pełne opcje, aby zobaczyć rzeczywiste polecenia. Aby uzyskać więcej informacji, zapoznaj się z dokumentacją systemu kompilacji.
