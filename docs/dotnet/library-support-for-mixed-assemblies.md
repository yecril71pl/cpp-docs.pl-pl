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
ms.openlocfilehash: 8c3fec26f3e41c3edd2346ac2e1b9b1f6b98ba33
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50069623"
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
