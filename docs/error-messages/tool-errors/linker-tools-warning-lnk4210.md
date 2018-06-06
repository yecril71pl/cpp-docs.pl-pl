---
title: Ostrzeżenie LNK4210 narzędzi konsolidatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4210
dev_langs:
- C++
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8700d9ad8eeef177de2f70f616cb0c06ba50670
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34703681"
---
# <a name="linker-tools-warning-lnk4210"></a>Ostrzeżenie LNK4210 narzędzi konsolidatora

> sekcja *sekcji* istnieje; może być nieobsługiwany statyczne inicjatory lub terminatory

## <a name="remarks"></a>Uwagi

Kodu wprowadziła statyczne inicjatory lub terminatory, ale kod uruchomienia biblioteki VCRuntime lub jego odpowiednik (co wymaga, aby uruchomić statyczne inicjatory lub terminatory) nie jest uruchamiane podczas uruchamiania aplikacji. Oto kilka przykładów kodu, który wymaga statyczne inicjatory lub terminatory:

- Zmienna klasy globalnej Konstruktor, destruktor lub tabeli funkcji wirtualnych.

- Zmienna globalna zainicjowany przy użyciu stałej się w czasie kompilacji.

Aby rozwiązać ten problem, wypróbuj jedną z następujących czynności:

- Usuń cały kod z statyczne inicjatory.

- Nie używaj [/noentry](../../build/reference/noentry-no-entry-point.md). Po usunięciu/noentry także mogą wymagać usunięcia [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) z wiersza polecenia konsolidatora.

- Jeśli kompilację używa/MT, dodać libcmt.lib, libvcruntime.lib i libucrt.lib z wierszem polecenia konsolidatora. Jeśli kompilację używa /MTd, należy dodać biblioteki libcmtd.lib, vcruntimed.lib i libucrtd.lib.

- Podczas przenoszenia z/CLR: pure kompilacji/CLR, Usuń [/Entry](../../build/reference/entry-entry-point-symbol.md) opcję z linii konsolidatora. To umożliwia Inicjalizacja CRT oraz umożliwia statyczne inicjatory do wykonania podczas uruchamiania aplikacji. **/CLR: pure** — opcja kompilatora jest przestarzałe w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

[/GS](../../build/reference/gs-buffer-security-check.md) — opcja kompilatora wymaga inicjowania przez `__security_init_cookie` funkcji. Inicjowanie tej znajduje się domyślnie w kodzie uruchamiania VCRuntime biblioteki, który jest uruchamiany w `_DllMainCRTStartup`.

- Projekt został zbudowany przy użyciu/Entry, a/Entry jest przekazywana funkcja innych niż `_DllMainCRTStartup`, należy wywołać funkcję `_CRT_INIT` zainicjować CRT. Jeśli biblioteki DLL używa/GS, wymaga statyczne inicjatory lub jest wywoływany w kontekście kodu MFC lub ATL tego samego połączenia jest niewystarczająca. Zobacz [biblioteki dll i Visual C++ zachowanie biblioteki wykonawczej](../../build/run-time-library-behavior.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md)
