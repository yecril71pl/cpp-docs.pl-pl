---
title: UNIX
ms.date: 11/04/2016
f1_keywords:
- unix
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
ms.openlocfilehash: d7f0cc1f9bbbfb1f950c7efc1371587d805d1e9e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480187"
---
# <a name="unix"></a>UNIX

Jeśli planujesz portu programów do systemu UNIX, należy przestrzegać następujących wytycznych:

- Nie usuwaj pliki nagłówkowe z podkatalogu SYS. Pliki nagłówkowe SYS można umieścić w innym miejscu tylko wtedy, gdy nie jest planowana transportu programów do systemu UNIX.

- Należy użyć ogranicznika ścieżka zgodne z systemem UNIX w procedur, które przyjmują ciągów reprezentujących ścieżki i nazwy plików jako argumenty. UNIX obsługuje tylko ukośnika (/) do tego celu, natomiast Win32, systemy operacyjne są obsługiwane zarówno ukośnik odwrotny (\\) i ukośnika (/). Dlatego ta dokumentacja używa ukośników zgodne z systemem UNIX jako ogranicznika ścieżka w `#include` instrukcji, na przykład. (Jednak system operacyjny Windows powłoki poleceń, CMD. Plik EXE, nie obsługuje ukośnik za pomocą poleceń, które wprowadzono w wierszu polecenia.)

- Użyj ścieżki i nazwy plików, który będzie działać poprawnie w systemie UNIX, który jest uwzględniana wielkość liter. Tabela (FAT) systemu plików FAT w systemach operacyjnych Win32 nie uwzględnia wielkości liter; zachowuje listach zawartości katalogów w przypadku systemu plików NTFS, ale ignoruje wielkość liter w poszukiwaniu plików i inne operacje systemu.

    > [!NOTE]
    >  W tej wersji programu Visual C++ zostało usunięte z opisy funkcji informacji na temat zgodności systemu UNIX.

## <a name="see-also"></a>Zobacz też

[Zgodność](../c-runtime-library/compatibility.md)