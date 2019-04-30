---
title: Ostrzeżenie LNK4210 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4210
helpviewer_keywords:
- LNK4210
ms.assetid: db48cff8-a2be-4a77-8d03-552b42c228fa
ms.openlocfilehash: 75376129ce0033c717a4da3074cee9de132d357d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395069"
---
# <a name="linker-tools-warning-lnk4210"></a>Ostrzeżenie LNK4210 narzędzi konsolidatora

> sekcja *sekcji* istnieje; może być nieobsługiwany statyczne inicjatory lub terminatory

## <a name="remarks"></a>Uwagi

Kod wprowadził statyczne inicjatory lub terminatory, ale kod uruchamiający biblioteki VCRuntime lub jej odpowiednik, (który wymaga, aby uruchomić statyczne inicjatory lub terminatory) nie jest uruchomione, podczas uruchamiania aplikacji. Poniżej przedstawiono kilka przykładów kodu, który wymaga statyczne inicjatory lub terminatory:

- Zmiennej globalnej klasy za pomocą Konstruktor, destruktor lub tabelę funkcji wirtualnych.

- Zmienna globalna zainicjowane ze stałą się w czasie kompilacji.

Aby rozwiązać ten problem, spróbuj wykonać jedną z następujących czynności:

- Usuń cały kod z statyczne inicjatory.

- Nie używaj [/noentry](../../build/reference/noentry-no-entry-point.md). Po usunięciu/noentry także mogą wymagać usunięcia [/nodefaultlib](../../build/reference/nodefaultlib-ignore-libraries.md) z wiersza polecenia konsolidatora.

- Jeśli kompilacja korzysta z/MT, należy dodać biblioteki libcmt.lib, libvcruntime.lib i libucrt.lib do wiersza polecenia konsolidatora. Jeśli kompilacja korzysta z/mtd, należy dodać biblioteki libcmtd.lib, vcruntimed.lib i libucrtd.lib.

- Podczas przenoszenia z/CLR: pure kompilacji/CLR, Usuń [/Entry](../../build/reference/entry-entry-point-symbol.md) opcji linii konsolidatora. To umożliwia inicjowanie CRT oraz umożliwia statyczne inicjatory do wykonania podczas uruchamiania aplikacji. **/CLR: pure** — opcja kompilatora jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

[/GS](../../build/reference/gs-buffer-security-check.md) — opcja kompilatora wymaga inicjowanie przez `__security_init_cookie` funkcji. Ten proces inicjowania jest zapewniany domyślnie w kod uruchamiający biblioteki VCRuntime pracująca w `_DllMainCRTStartup`.

- Jeśli projekt został skompilowany przy użyciu/Entry i/Entry jest przekazywany funkcji innych niż `_DllMainCRTStartup`, należy wywołać funkcję `_CRT_INIT` zainicjować CRT. To samo wywołanie jest niewystarczająca, jeśli biblioteka DLL wykorzystuje/GS, wymaga statyczne inicjatory lub jest wywoływana w kontekście kodu biblioteki ATL i MFC. Zobacz [bibliotek DLL i Visual C++ zachowanie biblioteki wykonawczej](../../build/run-time-library-behavior.md) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji konsolidatora](../../build/reference/linking.md)
