---
title: Aplikacje platformy uniwersalnej systemu Windows, środowisko uruchomieniowe Windows i środowiska wykonawczego języka C
ms.date: 02/02/2019
ms.assetid: 356d6d8d-76ee-4181-9ad0-6f24b2fede38
ms.openlocfilehash: 932b5388f2d1bf87f0d77ae1330fa3e613c9dca7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385125"
---
# <a name="uwp-apps-the-windows-runtime-and-the-c-run-time"></a>Aplikacje platformy uniwersalnej systemu Windows, środowisko uruchomieniowe Windows i środowiska wykonawczego języka C

Uniwersalnych aplikacji dla platformy Windows (UWP) są programy, które działają ze środowiska wykonawczego Windows, który jest wykonywany w systemie Windows 8. Środowisko wykonawcze Windows jest środowiskiem godne zaufania, które określa funkcje, zmienne i zasoby, które są dostępne dla aplikacji platformy uniwersalnej systemu Windows. Zgodnie z projektem ograniczenia środowiska uruchomieniowego Windows uniemożliwiają korzystania z większości funkcji biblioteki wykonawczej C (CRT) w aplikacjach platformy uniwersalnej systemu Windows.

Środowisko wykonawcze Windows nie obsługuje następujące funkcje CRT:

- Większość funkcji CRT, that are related to nieobsługiwanych funkcji.

   Na przykład aplikacji platformy uniwersalnej systemu Windows nie można utworzyć proces przy użyciu **exec** i **duplikowanie** rodzin procedury.

   Gdy funkcja CRT jest nieobsługiwana w aplikacji platformy uniwersalnej systemu Windows, że fakt została przedstawiona w artykule o jego.

- Najbardziej wielobajtowych znakowe i funkcje.

   Jednakże obsługiwane są teksty ANSI i Unicode.

- Zmienne środowiskowe.

- Pojęcie bieżącego katalogu roboczego.

- Platformy uniwersalnej systemu Windows aplikacji i bibliotek DLL, które są statycznie łączone do CRT i skompilowanych przy użyciu [/MT](../build/reference/md-mt-ld-use-run-time-library.md) lub `/MTd` opcje kompilatora.

   Oznacza to, aplikację, która korzysta z wielowątkowej, statycznej wersji CRT.

- Aplikacja, która powstała przy użyciu [/mdd](../build/reference/md-mt-ld-use-run-time-library.md) — opcja kompilatora.

   Oznacza to, debugowania, wielowątkowej i biblioteki DLL w wersji CRT. Takiej aplikacji nie jest obsługiwana w środowisku uruchomieniowym Windows.

Aby uzyskać pełną listę funkcji CRT, które nie są dostępne w aplikacji platformy uniwersalnej systemu Windows i sugestie dotyczące funkcji alternatywne, zobacz [funkcje CRT nieobsługiwane w aplikacjach platformy uniwersalnej Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="see-also"></a>Zobacz także

[Zgodność](../c-runtime-library/compatibility.md)<br/>
[Nieobsługiwane funkcje CRT środowiska uruchomieniowego systemu Windows](../c-runtime-library/windows-runtime-unsupported-crt-functions.md)<br/>
[Procedury czasu wykonywania języka Universal C według kategorii](../c-runtime-library/run-time-routines-by-category.md)<br/>
[Tworzenie aplikacji konsolowej Universal Windows Platform](/windows/uwp/launch-resume/console-uwp)
