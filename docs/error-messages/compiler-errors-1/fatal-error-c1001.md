---
title: Błąd krytyczny C1001
ms.date: 11/04/2016
f1_keywords:
- C1001
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
ms.openlocfilehash: ee0796260ac17613568912f0de235e9a1fd0702e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513896"
---
# <a name="fatal-error-c1001"></a>Błąd krytyczny C1001

> WEWNĘTRZNY ERROR(compiler file *file*, line *number*) KOMPILATORA

Kompilator nie może generować poprawny kod dla konstrukcję często z powodu kombinacji poszczególnych wyrażeń i opcji optymalizacji lub wystąpił problem podczas analizowania. Jeśli plik kompilatora wymienione ma czasu utc, czy C2 segment ścieżki, prawdopodobnie jest błędem optymalizacji. Jeśli plik ma cxxfe lub c1xx segmentu ścieżki lub jest msc1.cpp, to prawdopodobnie Błąd analizatora. Jeśli plik o nazwie jest cl.exe, nie ma żadnych innych informacji dostępna.

Można często rozwiązać problem optymalizacji, usuwając jeden lub więcej opcji optymalizacji. Aby określić, która opcja jest na pozycji błędu, Usuń opcji w czasie i skompiluj ponownie, dopóki zniknąć, komunikat o błędzie. Opcje najczęściej odpowiada [/Og (optymalizacje globalne)](../../build/reference/og-global-optimizations.md) i [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md). Po określeniu opcji optymalizacji odpowiada, możesz go wyłączyć, wokół funkcji, w którym występuje błąd przy użyciu [zoptymalizować](../../preprocessor/optimize.md) pragma i użyj opcji w pozostałej części modułu w dalszym ciągu. Aby uzyskać więcej informacji o opcjach optymalizacji, zobacz [najlepsze rozwiązania dotyczące optymalizacji](../../build/reference/optimization-best-practices.md).

Jeśli optymalizacji nie są odpowiedzialne za błąd, spróbuj ponowne napisanie wiersza, w której zgłaszany jest błąd lub kilka wierszy kodu wokół tego wiersza. Aby wyświetlić kod w sposób kompilator widzi on po przetwarzania wstępnego, można użyć [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) opcji.

Aby uzyskać więcej informacji na temat izolowania źródła błędu oraz zgłosić błąd wewnętrzny kompilatora do firmy Microsoft, zobacz [jak zgłosić Problem za pomocą zestawu narzędzi Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).