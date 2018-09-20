---
title: Obsługa bibliotek dla zestawów mieszanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/18/2018
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- msvcm90[d].dll
- mixed assemblies [C++], library support
- msvcmrt[d].lib
- libraries [C++], mixed assemblies
ms.assetid: 1229595c-9e9d-414d-b018-b4e4c727576d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 868cae6701e17c79c9856b3a16c63c1e25b67bda
ms.sourcegitcommit: 338e1ddc2f3869d92ba4b73599d35374cf1d5b69
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/20/2018
ms.locfileid: "46494520"
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
