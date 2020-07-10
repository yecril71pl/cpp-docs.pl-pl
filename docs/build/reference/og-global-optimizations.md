---
title: /Og (Optymalizacje globalne)
description: Opisuje przestarzałą opcję kompilatora MSVC/og, wcześniej używaną do włączania globalnych optymalizacji.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
ms.openlocfilehash: c1cab53ccb391bd7d6ca7660e2750f53aa7c72e4
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180854"
---
# <a name="og-global-optimizations"></a>`/Og`(Optymalizacje globalne)

Przestarzałe. Zapewnia optymalizację lokalną i globalną, alokację automatycznego rejestrowania i optymalizację pętli. Zalecamy użycie obu [ `/O1` (Minimalizuj rozmiar)](o1-o2-minimize-size-maximize-speed.md) lub [ `/O2` (maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md) .

## <a name="syntax"></a>Składnia

> **`/Og`**

## <a name="remarks"></a>Uwagi

**`/Og`** jest przestarzały. Te optymalizacje są teraz domyślnie włączone w przypadku włączenia dowolnych optymalizacji. Aby uzyskać więcej informacji na temat optymalizacji, zobacz [ `/O1` , `/O2` (Minimalizuj rozmiar, maksymalizuj szybkość)](o1-o2-minimize-size-maximize-speed.md)lub [ `/Ox` (Włącz optymalizację z największą szybkością)](ox-full-optimization.md).

Następujące optymalizacje są dostępne w obszarze **`/Og`** :

- Eliminacja lokalnych i globalnych wyrażeń podwyrażenia wspólnego

   W tej optymalizacji wartość wspólnego podwyrażenia jest obliczana raz. W poniższym przykładzie, jeśli wartości `b` i `c` nie zmieniają się między tymi trzema wyrażeniami, kompilator może przypisać obliczenie `b + c` do zmiennej tymczasowej i użyć tej zmiennej dla `b + c` :

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   W przypadku typowej optymalizacji podwyrażenia lokalnego kompilator analizuje krótkie sekcje kodu dla wspólnych podwyrażeń. W przypadku funkcji optymalizacji globalnej funkcji Common subexpression kompilator przeszukuje wszystkie funkcje dla wspólnych podwyrażeń.

- Automatyczne przydzielanie rejestru

   Ta optymalizacja umożliwia kompilatorowi przechowywanie często używanych zmiennych i podwyrażeń w rejestrach. `register`słowo kluczowe jest ignorowane.

- Optymalizacja pętli

   Ta optymalizacja usuwa niezmiennej subexpressions z treści pętli. Optymalna pętla zawiera tylko wyrażenia, których wartości zmieniają się w każdym wykonaniu pętli. W poniższym przykładzie wyrażenie `x + y` nie zmienia się w treści pętli:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   Po optymalizacji `x + y` jest obliczana raz, a nie za każdym razem, gdy pętla jest wykonywana:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   Optymalizacja pętli jest znacznie bardziej skuteczna, gdy kompilator nie może założyć aliasu, który można ustawić przy użyciu [`__restrict`](../../cpp/extension-restrict.md) , [`noalias`](../../cpp/noalias.md) lub [`restrict`](../../cpp/restrict.md) .

   > [!NOTE]
   > Można włączać lub wyłączać optymalizację globalną na podstawie funkcji i funkcji za pomocą `optimize` dyrektywy pragma wraz z `g` opcją.

Aby uzyskać powiązane informacje, zobacz [ `/Oi` (generowanie funkcji wewnętrznych)](oi-generate-intrinsic-functions.md) i [ `/Ox ` (Włączanie optymalizacji z największą szybkością)](ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Wprowadź opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
