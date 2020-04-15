---
title: Błąd krytyczny C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: 83135b77ceb75b4c2b05211260d1aed8fac6777f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320302"
---
# <a name="fatal-error-c1060"></a>Błąd krytyczny C1060

kompilator jest poza miejscem na stertę

System operacyjny lub biblioteka czasu wykonywania nie może wypełnić żądania pamięci.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Aby naprawić ten błąd, wypróbuj następujące możliwe rozwiązania

1. Jeśli kompilator generuje również błędy [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) i [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), użyj opcji kompilatora [/Zm,](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) aby obniżyć limit alokacji pamięci. Więcej miejsca na stercie jest dostępna dla aplikacji, jeśli obniżysz alokację pozostałej pamięci.

   Jeśli opcja [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) jest już ustawiona, spróbuj ją usunąć. Miejsce na stercie może zostać wyczerpane, ponieważ limit alokacji pamięci określony w opcji jest zbyt wysoki. Kompilator używa domyślnego limitu po usunięciu opcji [/Zm.](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md)

1. Jeśli kompilujesz na platformie 64-bitowej, użyj zestawu narzędzi kompilatora 64-bitowego. Aby uzyskać więcej informacji, zobacz [Jak: Włączanie 64-bitowego zestawu narzędzi Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. W 32-bitowym systemie Windows spróbuj użyć przełącznika boot.ini [o gb/3 GB.](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200)

1. Zwiększ rozmiar pliku wymiany systemu Windows.

1. Zamknij inne uruchomione programy.

1. Wyeliminuj niepotrzebne pliki dołączane.

1. Wyeliminuj niepotrzebne zmienne globalne, na przykład, przydzielając pamięć dynamicznie zamiast deklarowania dużej tablicy.

1. Usuń nieużywane deklaracje.

1. Podziel bieżący plik na mniejsze pliki.
