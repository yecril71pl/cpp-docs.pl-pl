---
title: Typowe problemy przy migracji Visual C++ w wersji 64-bitowej
ms.date: 11/04/2016
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 1eb5a7f8d708d16241f1637269f31563378f084d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468773"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Typowe problemy przy migracji Visual C++ w wersji 64-bitowej

Korzystając z programu Visual C++ do tworzenia aplikacji do uruchomienia w 64-bitowym systemie operacyjnym Windows, należy pamiętać o następujących kwestiach:

- `int` i `long` wartości 32-bitowy na 64-bitowych systemach operacyjnych Windows. Dla programów, które mają zostać kompilacji dla platform 64-bitowych należy zachować ostrożność nie można przypisać wskaźniki do zmiennych 32-bitowych. Wskaźniki są 64-bit na platformach 64-bitowych, a obetnie wartość wskaźnika, w przypadku przypisania do zmiennej 32-bitowych.

- `size_t`, `time_t`, i `ptrdiff_t` wartości 64-bitowym na 64-bitowych systemach operacyjnych Windows.

- `time_t` jest wartością 32-bitowego na 32-bitowych systemach operacyjnych Windows w wersjach Visual C++ starszych niż Visual C++ 2005. `time_t` jest teraz 64-bitową liczbę całkowitą, domyślnie. Aby uzyskać więcej informacji, zobacz [zarządzanie czasem](../c-runtime-library/time-management.md).

   Należy pamiętać o którym kod ma `int` wartość i przetwarza je jako `size_t` lub `time_t` wartość. Istnieje możliwość, że liczba można zwiększać będzie większy niż wartość liczby 32-bitowej i dane zostaną obcięte, gdy jest przekazywany do `int` magazynu.

%X (szesnastkowa `int` format) `printf` modyfikator nie będzie działać zgodnie z oczekiwaniami na 64-bitowym systemie operacyjnym Windows. Będzie on działać tylko na pierwsze 32 bity na wartość, która jest przekazywana do niego.

- % I32x umożliwia wyświetlenie 32-bitowy typ całkowity w formacie szesnastkowym.

- % I64x umożliwia wyświetlenie 64-bitowy typ całkowity w formacie szesnastkowym.

- %P (w formacie szesnastkowy dla wskaźnika) będzie działać zgodnie z oczekiwaniami na 64-bitowym systemie operacyjnym Windows.

Aby uzyskać więcej informacji, zobacz:

- [Opcje kompilatora](../build/reference/compiler-options.md)

- [Wskazówki dotyczące migracji](/windows/desktop/WinProg64/migration-tips)

## <a name="see-also"></a>Zobacz też

[Konfigurowanie Visual C++ dla wersji 64-bitowych, platformy docelowe x64](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)