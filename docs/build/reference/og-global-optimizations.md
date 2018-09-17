---
title: -Og (optymalizacje globalne) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/22/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs:
- C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8443ae8111476cdd3339982c8df0b4b7e3e9c475
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722530"
---
# <a name="og-global-optimizations"></a>/Og (Optymalizacje globalne)

Przestarzałe. Udostępnia lokalne i globalne optymalizacje, automatyczne rejestrowanie alokacji i optymalizacji pętli. Firma Microsoft zaleca, należy użyć [/O1 (Minimalizuj rozmiar)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub [/O2 (Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) zamiast tego.

## <a name="syntax"></a>Składnia

> /Og

## <a name="remarks"></a>Uwagi

**/Og** jest przestarzała. Optymalizacje te są teraz ogólnie domyślnie włączone. Aby uzyskać więcej informacji na temat optymalizacji, zobacz [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub [OX (Włącz większość optymalizacji szybkości)](../../build/reference/ox-full-optimization.md).

Następujące optymalizacje są dostępne w obszarze **/Og**:

- Lokalne i globalne eliminacja wspólnych podwyrażeń

   W tego rodzaju optymalizacji jeden raz jest obliczana wartość wspólnych podwyrażeń. W poniższym przykładzie Jeśli wartości `b` i `c` nie zmienił się od trzech wyrażeń, kompilator może przypisać do obliczania `b + c` do zmiennej tymczasowej i Zastąp zmienną dla `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

   Lokalne wspólnej optymalizacji Podwyrażenie kompilator sprawdza krótkich fragmentów kodu dla typowych podwyrażenia. Globalne wspólnej optymalizacji Podwyrażenie kompilator przeszukuje cały funkcje dla typowych podwyrażenia.

- Automatyczna alokacja rejestru

   Tego rodzaju optymalizacji umożliwia kompilatorowi do przechowywania często używanych zmiennych i podwyrażenia w rejestrach; `register` — słowo kluczowe jest ignorowana.

- Optymalizacji pętli

   Tego rodzaju optymalizacji usuwa niezmiennej podwyrażenia z treści pętli. Optymalne pętla zawiera tylko wyrażenia, w których wartości zmieniają się za pomocą każdego wykonania pętli. W poniższym przykładzie wyrażenie `x + y` nie zmienia się w ciele pętli:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

   Po optymalizacji `x + y` jest obliczana raz zamiast każdym wykonaniu pętli:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

   Optymalizacji pętli jest znacznie bardziej efektywne w przypadku, gdy kompilator może przyjąć aliasing, możesz ustawić przy użyciu [element __restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), lub [ograniczyć](../../cpp/restrict.md).

   > [!NOTE]
   > Można włączyć lub wyłączyć optymalizację globalną na temat korzystania z poszczególnych funkcji przez funkcję `optimize` pragma wraz z `g` opcji.

Aby uzyskać powiązane informacje, zobacz [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md) i [OX (Włącz większość optymalizacji szybkości)](../../build/reference/ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcję kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)

[Opcje kompilatora](../../build/reference/compiler-options.md)

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)