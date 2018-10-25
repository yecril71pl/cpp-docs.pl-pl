---
title: Błąd krytyczny C1060 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1060
dev_langs:
- C++
helpviewer_keywords:
- C1060
ms.assetid: feaf305c-c84c-4160-b974-50e283412849
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09d9c0292840daf65effca09775ff85a156b00f8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50053919"
---
# <a name="fatal-error-c1060"></a>Błąd krytyczny C1060

Kompilator nie ma miejsca na stercie

System operacyjny lub biblioteki wykonawczej nie można wypełnić żądanie pamięci.

### <a name="to-fix-this-error-try-the-following-possible-solutions"></a>Aby naprawić ten błąd, spróbuj poniższymi możliwymi rozwiązaniami

1. Jeśli kompilator generuje również błędy [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) i [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md), użyj [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) — opcja kompilatora obniżyć limit alokacji pamięci. Więcej miejsca na stercie jest dostępne dla aplikacji, jeśli obniżyć pozostałych alokacji pamięci.

   Jeśli [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) już ustawiono opcję, spróbuj go usunąć. Mogą się wyczerpać miejsca na stercie, ponieważ limit alokacji pamięci, określonego w opcji jest zbyt duża. Kompilator używa domyślny limit maksymalnej, jeśli usuniesz [/Zm](../../build/reference/zm-specify-precompiled-header-memory-allocation-limit.md) opcji.

1. Jeśli kompilujesz na platformie 64-bitowej, należy użyć narzędzi 64-bitowego kompilatora. Aby uzyskać informacje, zobacz [porady: Włączanie 64-bitowego zestawu narzędzi Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md).

1. W 32-bitowa Windows, spróbuj użyć [3 GB](https://support.microsoft.com/help/833721/available-switch-options-for-the-windows-xp-and-the-windows-server-200) przełącznika pliku boot.ini.

1. Zwiększenie rozmiaru pliku wymiany Windows.

1. Zamknij inne uruchomione programy.

1. Wyeliminuj niepotrzebne pliki dołączane.

1. Wyeliminuj niepotrzebne zmienne globalne, na przykład poprzez przydzielanie pamięci dynamicznie zamiast deklarowania dużej tablicy.

1. Usuń nieużywane deklaracje.

9. Podziel bieżący plik na mniejsze pliki.