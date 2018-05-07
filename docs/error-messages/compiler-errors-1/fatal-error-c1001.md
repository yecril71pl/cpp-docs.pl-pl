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
ms.openlocfilehash: f605dd7e4892c4a8b57e544ed857257be72f020d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fatal-error-c1001"></a>Błąd krytyczny C1001

> WEWNĘTRZNY ERROR(compiler file *file*, line *number*) KOMPILATORA  
  
Kompilator nie może wygenerować prawidłowego kodu dla konstrukcji, często z powodu kombinacji określonego wyrażenia i opcję optymalizacji lub wystąpił problem podczas analizy. Jeśli plik kompilatora wymienione ma czasu utc, czy C2 segment ścieżki, prawdopodobnie jest błędem optymalizacji. Jeśli plik ma cxxfe lub c1xx segment ścieżki lub jest msc1.cpp, prawdopodobnie jest błąd analizatora. Jeśli plik o nazwie cl.exe, nie ma żadnych innych informacji dostępne.  

Można często rozwiązać problem optymalizacji przez usunięcie jednego lub więcej opcji optymalizacji. Aby ustalić, która opcja jest uszkodzone, Usuń opcji w czasie i skompilować ją ponownie, dopóki komunikat o błędzie zniknie. Dostępne są następujące opcje, które są najczęściej odpowiedzialny [/Og (optymalizacje globalne)](../../build/reference/og-global-optimizations.md) i [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md). Po określeniu opcji optymalizacji odpowiada, można ją wyłączyć, wokół funkcja, której wystąpił błąd przy użyciu [zoptymalizować](../../preprocessor/optimize.md) pragma i Kontynuuj użyć opcji dla całego modułu. Aby uzyskać więcej informacji na temat opcji optymalizacji, zobacz [najlepsze praktyki optymalizacji](../../build/reference/optimization-best-practices.md).

Jeśli optymalizacje nie są odpowiedzialne za błąd, spróbuj ponowne zapisywanie wiersza, w którym zgłaszany jest błąd lub kilku wierszy kodu otaczającego tego wiersza. Aby wyświetlić kod sposób kompilator widzi ona po przetwarzania wstępnego, można użyć [/P (Przetwarzaj wstępnie do pliku)](../../build/reference/p-preprocess-to-a-file.md) opcji.

Aby uzyskać więcej informacji na temat izolowania źródła błędu oraz Zgłoś błąd wewnętrzny kompilatora do firmy Microsoft, zobacz [jak zgłosić Problem z zestawu narzędzi programu Visual C++](../../how-to-report-a-problem-with-the-visual-cpp-toolset.md).