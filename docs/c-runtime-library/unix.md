---
title: UNIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- unix
dev_langs:
- C++
helpviewer_keywords:
- UNIX
- POSIX compatibility
- POSIX file names
- UNIX, compatibility
ms.assetid: 40792414-7a5b-415d-bfa8-2bfb1ebb3731
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2403eb0fbe19f83df3909c9d8b765f00fed82c8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409322"
---
# <a name="unix"></a>UNIX
Jeśli planujesz portu programy do systemu UNIX, wykonaj następujące wytyczne:  
  
-   Nie należy usuwać pliki nagłówkowe z podkatalogu SYS. Pliki nagłówkowe SYS można umieścić w innym miejscu tylko wtedy, gdy nie zamierzasz transportu programy do systemu UNIX.  
  
-   Użyj zgodnych z systemem UNIX ogranicznika ścieżki w procedur, które pobierają ciągi reprezentujący ścieżki i nazwy plików jako argumenty. UNIX obsługuje tylko ukośnika (/) w tym celu należy Win32 systemy operacyjne obsługują zarówno ukośnik odwrotny (\\) i ukośnika (/). W związku z tym ta dokumentacja używa ukośniki zgodnych z systemem UNIX jako ograniczników ścieżki w `#include` instrukcje, na przykład. (Jednak system operacyjny Windows poleceń powłoki, CMD. EXE, nie obsługuje ukośnik w poleceniach wprowadzona w wierszu polecenia.)  
  
-   Użyj ścieżki i nazwy plików, który będzie działać poprawnie w systemie UNIX, który jest uwzględniana wielkość liter. Tabela (FAT) systemu plików FAT w systemach operacyjnych Win32 nie jest uwzględniana; zachowuje wielkość liter na listach zawartości katalogów systemu plików NTFS, ale ignoruje wielkość liter w poszukiwaniu plików i innych operacji systemu.  
  
    > [!NOTE]
    >  W tej wersji programu Visual C++ informacje o zgodności systemu UNIX została usunięta z opisy funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Zgodność](../c-runtime-library/compatibility.md)