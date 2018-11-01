---
title: Obsługa bibliotek dla zestawów mieszanych
ms.date: 09/18/2018
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
ms.openlocfilehash: 42116c09d5b31cf669eb6d5d1e75eae60b2610a7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474762"
---
# <a name="library-support-for-mixed-assemblies"></a>Obsługa bibliotek dla zestawów mieszanych

Visual C++ obsługuje używanie standardowej biblioteki C++, biblioteki środowiska uruchomieniowego języka C (CRT), ATL i MFC dla aplikacje skompilowane przy użyciu [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../build/reference/clr-common-language-runtime-compilation.md). Dzięki temu istniejące aplikacje korzystające z tych bibliotek do użycia jak również funkcje środowiska .NET Framework.

> [!IMPORTANT]
> **/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

Ta obsługa obejmuje następujące biblioteki DLL i importowania:

- .Lib Msvcmrt [d] Jeśli kompilujesz z opcją **/CLR**. Zestawy mieszane link do tej biblioteki importu.

Ta funkcja zapewnia kilka korzyści związanych z nimi:

- CRT i standardowej biblioteki języka C++ są dostępne dla kodu mieszanego. CRT i standardowej biblioteki języka C++, pod warunkiem nie są możliwe do zweryfikowania; ostatecznie wywołania nadal są kierowane do tego samego CRT i standardowej biblioteki języka C++, w przypadku korzystania z kodu natywnego.

- Poprawne ujednoliconej obsługi wyjątków w mieszanych obrazów.

- Statyczne inicjowanie zmienne języka C++ w obrazach mieszane.

- Obsługa zmiennych per-AppDomain i na proces w kodzie zarządzanym.

- Rozwiązanie problemów blokady modułu ładującego, które dotyczą mieszanych bibliotek DLL, skompilowany w Visual Studio 2003 i wcześniejszych wersjach.

Ponadto ta funkcja prezentuje następujące ograniczenia:

- Tylko model CRT DLL jest obsługiwana dla kodu skompilowanego z **/CLR**. Brak statycznego bibliotek CRT, które obsługują **/CLR** kompilacji.

## <a name="see-also"></a>Zobacz także

- [Zestawy mieszane (natywne i zarządzane)](../dotnet/mixed-native-and-managed-assemblies.md)
