---
title: Błąd krytyczny C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: 91753a49498548b4e523cd8564ee7a7ca7a3b373
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406954"
---
# <a name="fatal-error-c1076"></a>Błąd krytyczny C1076

> limit kompilatora : limit sterty wewnętrznej osiągnięty; użyj /Zm, aby określić wyższy limit

Ten błąd może być spowodowany przez zbyt wiele symboli lub zbyt wiele wystąpień szablonu. Począwszy od programu Visual Studio 2015, ten komunikat ma mogą wynikać z dużego wykorzystania pamięci wirtualnej Windows spowodowane zbyt wielu procesów kompilacji równoległych. W takim przypadku zalecenie, aby używać **/Zm** opcji mają być ignorowane, chyba że używasz `#pragma hdrstop` dyrektywy.

Aby rozwiązać ten błąd:

1. Jeśli korzysta z prekompilowanego pliku nagłówkowego `#pragma hdrstop` dyrektywy, użyj [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opcję, aby ustawić limit pamięci kompilatora na wartość określoną w [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) komunikat o błędzie. Aby uzyskać więcej informacji o tym, jak ustawić tę wartość w programie Visual Studio, zobacz sekcję Uwagi w [/Zm (Określ wstępnie skompilowany nagłówek Memory Allocation Limit)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Należy wziąć pod uwagę, co zmniejsza liczbę równoległych procesów określone za pomocą **/maxcpucount** opcji do programu MSBUILD. Plik EXE w połączeniu z **/MP** opcji cl. PLIK EXE. Aby uzyskać więcej informacji, zobacz [Prekompilowanego nagłówka (PCH) zagadnienia i zalecenia dotyczące](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Jeśli używasz kompilatorów dla hostów 32-bitowych w 64-bitowym systemie operacyjnym, użyj kompilatorów dla hostów 64-bitowych. Aby uzyskać więcej informacji, zobacz [jak: Włączanie 64-bitowego zestawu narzędzi Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Wyeliminuj niepotrzebne pliki dołączane.

1. Wyeliminuj niepotrzebne zmienne globalne — na przykład poprzez przydzielanie pamięci dynamicznie zamiast deklarowania dużej tablicy.

1. Usuń nieużywane deklaracje.

Jeśli C1076 pojawia się natychmiast po uruchomieniu kompilacji, wartość określona dla **/Zm** prawdopodobnie jest zbyt duża dla Twojego programu. Zmniejsz **/Zm** wartości.