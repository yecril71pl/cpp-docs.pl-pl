---
title: Błąd krytyczny C1076
ms.date: 03/08/2019
f1_keywords:
- C1076
helpviewer_keywords:
- C1076
ms.assetid: 84ac1180-3e8a-48e8-9f77-7f18a778b964
ms.openlocfilehash: ca5117342d406983e8cba675c2589d2431d09d38
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204181"
---
# <a name="fatal-error-c1076"></a>Błąd krytyczny C1076

> limit kompilatora : limit sterty wewnętrznej osiągnięty; użyj /Zm, aby określić wyższy limit

Ten błąd może być spowodowany przez zbyt wiele symboli lub zbyt wiele wystąpień szablonu. Począwszy od programu Visual Studio 2015, ten komunikat może być spowodowany przez zbyt wiele równoległych procesów kompilacji. W takim przypadku zalecenie dotyczące korzystania z opcji **/zm** powinno być ignorowane, chyba że używana jest dyrektywa `#pragma hdrstop`.

Aby rozwiązać ten błąd:

1. Jeśli prekompilowany nagłówek używa dyrektywy `#pragma hdrstop`, użyj opcji [/zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) , aby ustawić limit pamięci kompilatora na wartość określoną w komunikacie o błędzie [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) . Aby uzyskać więcej informacji dotyczących sposobu ustawiania tej wartości w programie Visual Studio, zobacz sekcję Uwagi w [/zm (Określ limit alokacji pamięci prekompilowanego nagłówka)](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md).

1. Rozważ zmniejszenie liczby procesów równoległych określonych przy użyciu opcji **/maxcpucount** do programu MSBuild. EXE w połączeniu z opcją **/MP** do CL. EXE. Aby uzyskać więcej informacji, zobacz [artykuły prekompilowanego nagłówka (pch) i zalecenia](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

1. Jeśli używasz kompilatorów dla hostów 32-bitowych w 64-bitowym systemie operacyjnym, użyj kompilatorów dla hostów 64-bitowych. Aby uzyskać więcej informacji, zobacz [How to: Enable a 64-bitowy C++ zestaw narzędzi wizualnych w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. Wyeliminuj niepotrzebne pliki dołączane.

1. Wyeliminuj niepotrzebne zmienne globalne — na przykład poprzez przydzielanie pamięci dynamicznie zamiast deklarowania dużej tablicy.

1. Usuń nieużywane deklaracje.

Jeśli C1076 występuje natychmiast po rozpoczęciu kompilacji, wartość określona dla **/zm** jest prawdopodobnie zbyt wysoka dla programu. Zmniejsz wartość **/zm** .
