---
title: Błąd krytyczny C1001 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1001
dev_langs:
- C++
helpviewer_keywords:
- C1001
ms.assetid: 5736cdb3-22c8-4fad-aa85-d5e0d2b232f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6363694dbd7f1a7ebfcd58cad030dfecf7f38397
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46098202"
---
# <a name="fatal-error-c1001"></a>Błąd krytyczny C1001

> WEWNĘTRZNY ERROR(compiler file *file*, line *number*) KOMPILATORA

Kompilator nie może generować poprawny kod dla konstrukcję często z powodu kombinacji poszczególnych wyrażeń i opcji optymalizacji lub wystąpił problem podczas analizowania. Jeśli plik kompilatora wymienione ma czasu utc, czy C2 segment ścieżki, prawdopodobnie jest błędem optymalizacji. Jeśli plik ma cxxfe lub c1xx segmentu ścieżki lub jest msc1.cpp, to prawdopodobnie Błąd analizatora. Jeśli plik o nazwie jest cl.exe, nie ma żadnych innych informacji dostępna.

Można często rozwiązać problem optymalizacji, usuwając jeden lub więcej opcji optymalizacji. Aby określić, która opcja jest na pozycji błędu, Usuń opcji w czasie i skompiluj ponownie, dopóki zniknąć, komunikat o błędzie. Opcje najczęściej odpowiada [/Og (optymalizacje globalne)](../../build/reference/og-global-optimizations.md) i [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md). Po określeniu opcji optymalizacji odpowiada, możesz go wyłączyć, wokół funkcji, w którym występuje błąd przy użyciu [zoptymalizować](../../preprocessor/optimize.md) pragma i użyj opcji w pozostałej części modułu w dalszym ciągu. Aby uzyskać więcej informacji o opcjach optymalizacji, zobacz [najlepsze rozwiązania dotyczące optymalizacji](../../build/reference/optimization-best-practices.md).

Jeśli optymalizacji nie są odpowiedzialne za błąd, spróbuj ponowne napisanie wiersza, w której zgłaszany jest błąd lub kilka wierszy kodu wokół tego wiersza. Aby wyświetlić kod w sposób kompilator widzi on po przetwarzania wstępnego, można użyć [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) opcji.

Aby uzyskać więcej informacji na temat izolowania źródła błędu oraz zgłosić błąd wewnętrzny kompilatora do firmy Microsoft, zobacz [jak zgłosić Problem za pomocą zestawu narzędzi Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).