---
title: Błąd krytyczny C1060
ms.date: 11/04/2016
f1_keywords:
- C1060
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
ms.openlocfilehash: f1a7c3ccab716a9281d4520f4c5fce2afff60187
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204441"
---
# <a name="fatal-error-c1060"></a>Błąd krytyczny C1060

Kompilator nie ma miejsca na stercie

System operacyjny lub Biblioteka wykonawcza nie może wypełnić żądania dotyczącego pamięci.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Aby naprawić ten błąd, wypróbuj następujące możliwe rozwiązania

1. Jeśli kompilator wystawia także błędy [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) i [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), należy użyć opcji kompilatora [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) , aby obniżyć limit przydziału pamięci. W przypadku obniżenia przydziału reszty pamięci dla aplikacji jest dostępna większa przestrzeń sterty.

   Jeśli opcja [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) jest już ustawiona, spróbuj ją usunąć. Przestrzeń sterty może być wyczerpana, ponieważ limit alokacji pamięci określony w opcji jest zbyt duży. W przypadku usunięcia opcji [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) kompilator używa domyślnego limitu.

1. Jeśli kompilujesz na platformie 64-bitowej, użyj zestawu narzędzi kompilatora 64-bitowego. Aby uzyskać więcej informacji, zobacz [How to: Enable a 64- C++ bitowy zestaw narzędzi wizualnych w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. W 32-bitowej wersji systemu Windows spróbuj użyć przełącznika pliku Boot. ini programu [/3gb](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) .

1. Zwiększ rozmiar pliku wymiany systemu Windows.

1. Zamknij inne uruchomione programy.

1. Wyeliminuj niepotrzebne pliki dołączane.

1. Eliminuj niepotrzebne zmienne globalne, na przykład przez przydzielanie pamięci dynamicznie zamiast deklarującej dużą tablicę.

1. Usuń nieużywane deklaracje.

9. Podziel bieżący plik na mniejsze pliki.
