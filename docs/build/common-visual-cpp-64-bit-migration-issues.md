---
title: Typowe problemy przy migracji Visual C++ w wersji 64-bitowej
ms.date: 05/06/2019
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: 004fe7ace6102feecbcb2f542b5b93268ae2f868
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493312"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Typowe problemy przy migracji Visual C++ w wersji 64-bitowej

W przypadku tworzenia aplikacji do C++ uruchamiania w 64-bitowym systemie operacyjnym Windows przy użyciu programu Microsoft Compiler należy pamiętać o następujących kwestiach:

- A i a `long` są 32-bitowe wartości w 64-bitowych systemach operacyjnych Windows. `int` W przypadku programów, które mają zostać skompilowane dla platform 64-bitowych, należy uważać, aby nie przypisywać wskaźników do zmiennych 32-bitowych. Wskaźniki są 64-bitowe na platformach 64-bitowych, a wartość wskaźnika zostanie obcinana, jeśli zostanie przypisana do zmiennej 32-bitowej.

- `size_t`, `time_t` i`ptrdiff_t` są 64-bitowe wartości w 64-bitowych systemach operacyjnych Windows.

- `time_t`to 32-bitowa wartość w 32-bitowych systemach operacyjnych Windows w programie Visual Studio 2005 i starszych. `time_t`jest teraz domyślnie 64-bitową liczbą całkowitą. Aby uzyskać więcej informacji, zobacz [Zarządzanie czasem](../c-runtime-library/time-management.md).

   Należy pamiętać, gdzie kod pobiera `int` wartość i przetwarza ją `size_t` jako `time_t` wartość. Możliwe, że liczba może wzrosnąć do wartości większej niż 32-bitowa, a dane zostaną obcięte, `int` gdy zostanie przeniesiona z powrotem do magazynu.

Modyfikator% x (szesnastkowo `int` format) `printf` nie będzie działać zgodnie z oczekiwaniami w 64-bitowym systemie operacyjnym Windows. Będzie działać tylko w przypadku pierwszych 32 bitów wartości, która jest przenoszona do niej.

- Użyj elementu% I32x, aby wyświetlić 32-bitowy typ całkowity w formacie szesnastkowym.

- Użyj elementu% I64x, aby wyświetlić 64-bitowy typ całkowity w formacie szesnastkowym.

- % P (format szesnastkowy wskaźnika) będzie działać zgodnie z oczekiwaniami w 64-bitowym systemie operacyjnym Windows.

Aby uzyskać więcej informacji, zobacz:

- [Opcje kompilatora MSVC](reference/compiler-options.md)

- [Wskazówki dotyczące migracji](/windows/win32/WinProg64/migration-tips)

## <a name="see-also"></a>Zobacz także

[Konfigurowanie C++ projektów dla 64-bitowych, docelowych procesorów x64](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](../porting/visual-cpp-porting-and-upgrading-guide.md)
