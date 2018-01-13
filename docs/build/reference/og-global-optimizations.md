---
title: -Og (optymalizacje globalne) | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.GlobalOptimizations
- /og
dev_langs: C++
helpviewer_keywords:
- -Og compiler option [C++]
- global optimizations compiler option [C++]
- automatic register allocation
- /Og compiler option [C++]
- loop structures, optimizing
- common subexpression elimination
- Og compiler option [C++]
ms.assetid: d10630cc-b9cf-4e97-bde3-8d7ee79e9435
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 196e89a958ce49bf5e0087d98d2f40ada210cc87
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="og-global-optimizations"></a>/Og (Optymalizacje globalne)

Przestarzałe. Udostępnia lokalne i globalne optymalizacje, automatyczne rejestru alokacji i pętla optymalizacji. Zalecane jest użycie albo [/O1 (Minimalizuj rozmiar)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub [/O2 (Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) zamiast tego.

## <a name="syntax"></a>Składnia

> /Og

## <a name="remarks"></a>Uwagi

**/Og** jest przestarzały. Te optymalizacje są teraz zazwyczaj domyślnie włączone. Aby uzyskać więcej informacji o optymalizacji, zobacz [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) lub [OX (Włącz najbardziej prędkości optymalizacji)](../../build/reference/ox-full-optimization.md).

Następujące funkcje optymalizacji są dostępne w ramach **/Og**:

- Lokalne i globalne eliminacja wspólnych podwyrażeń

     W tej optymalizacji wartości typowych Podwyrażenie jest obliczany raz. W poniższym przykładzie Jeśli wartości `b` i `c` nie należy zmieniać między trzy wyrażenia, kompilator można przypisać do obliczania `b + c` do zmiennej tymczasowej i Zastąp zmienną dla `b + c`:

    ```C
    a = b + c;
    d = b + c;
    e = b + c;
    ```

     Lokalne wspólnej optymalizacji Podwyrażenie kompilator sprawdza krótkich fragmentów kodu dla typowych użyto. Globalne wspólnej optymalizacji Podwyrażenie kompilator wyszukuje całego funkcje dla typowych zakresie.

- Automatyczna alokacja rejestru

     Tego rodzaju optymalizacji umożliwia kompilatorowi zmienne do przechowywania często używanych i użyto w rejestrach; `register` — słowo kluczowe jest ignorowana.

- Optymalizacja pętli

     Tego rodzaju optymalizacji usuwa niezmiennej użyto z treści pętli. Optymalne pętla zawiera tylko wyrażenia, którego wartości zmienić za pomocą każdej wykonywania pętli. W poniższym przykładzie wyrażenie `x + y` nie zmienia się w treści pętli:

    ```C
    i = -100;
    while( i < 0 ) {
        i += x + y;
    }
    ```

     Po optymalizacji `x + y` jest obliczana raz zamiast zawsze pętla jest wykonywana:

    ```C
    i = -100;
    t = x + y;
    while( i < 0 ) {
        i += t;
    }
    ```

     Optymalizacja pętli jest bardziej efektywne, gdy kompilator może przyjmować nie aliasów, który ustawia z [__restrict](../../cpp/extension-restrict.md), [noalias](../../cpp/noalias.md), lub [ograniczyć](../../cpp/restrict.md).

    > [!NOTE]
    > Można włączyć lub wyłączyć optymalizacje globalne na poszczególnych funkcji funkcji przy użyciu `optimize` pragma razem z `g` opcji.

 Aby uzyskać odpowiednie informacje, zobacz [/Oi (Generuj funkcje wewnętrzne)](../../build/reference/oi-generate-intrinsic-functions.md) i [OX (Włącz najbardziej prędkości optymalizacji)](../../build/reference/ox-full-optimization.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** strony właściwości.

1. Wybierz opcję kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)

[Opcje kompilatora](../../build/reference/compiler-options.md)

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)