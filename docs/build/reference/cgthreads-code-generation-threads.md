---
title: /cgthreads (Wątki generowania kodu)
ms.date: 07/31/2020
f1_keywords:
- /cgthreads
helpviewer_keywords:
- /cgthreads compiler option (C++)
- -cgthreads compiler option (C++)
- cgthreads compiler option (C++)
- cgthreads
ms.assetid: 64bc768c-6caa-4baf-9dea-7cfa1ffb01c2
ms.openlocfilehash: 319a42ab68f02df6019ff283f1039ef3d561c4a0
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520878"
---
# <a name="cgthreads-code-generation-threads"></a>`/cgthreads`(Wątki generowania kodu)

Ustawia liczbę cl.exe wątków do użycia na potrzeby optymalizacji i generowania kodu.

## <a name="syntax"></a>Składnia

> **`/cgthreads1`**\
> **`/cgthreads2`**\
> **`/cgthreads3`**\
> **`/cgthreads4`**\
> **`/cgthreads5`**\
> **`/cgthreads6`**\
> **`/cgthreads7`**\
> **`/cgthreads8`**

## <a name="arguments"></a>Argumenty

**`cgthreadsN`**\
Maksymalna liczba wątków używanych przez cl.exe, gdzie *N* to liczba z zakresu od 1 do 8.

## <a name="remarks"></a>Uwagi

**`cgthreads`** Opcja określa maksymalną liczbę wątków, cl.exe równolegle używa dla faz optymalizacji i generowania kodu kompilacji. Należy zauważyć, że między **`cgthreads`** i argumentem *Number* nie może znajdować się spacja. Domyślnie cl.exe używa czterech wątków, tak jak gdyby **`/cgthreads4`** zostały określone. Jeśli jest dostępnych więcej rdzeni procesora, większa wartość *liczbowa* może skrócić czas kompilacji. Ta opcja jest szczególnie przydatna w przypadku połączenia z programem [ `/GL` (Optymalizacja całego programu)](gl-whole-program-optimization.md).

Dla kompilacji można określić wiele poziomów równoległości. Przełącznik msbuild.exe **`/maxcpucount`** określa liczbę procesów programu MSBuild, które mogą być uruchamiane równolegle. Flaga kompilatora [ `/MP` (kompilacja z wieloma procesami)](mp-build-with-multiple-processes.md) określa liczbę procesów cl.exe, które jednocześnie kompilują pliki źródłowe. **`cgthreads`** Opcja określa liczbę wątków używanych przez każdy proces cl.exe. Procesor może pracować tylko z wieloma wątkami w tym samym czasie, w którym występują rdzenie procesora. Nie jest przydatne Określanie większych wartości dla wszystkich tych opcji w tym samym czasie i może być counterproductive. Aby uzyskać więcej informacji o tym, jak kompilować projekty równolegle, zobacz [kompilowanie wielu projektów równolegle](/visualstudio/msbuild/building-multiple-projects-in-parallel-with-msbuild).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **Configuration Properties**  >  stronę właściwości konfiguracja wiersza polecenia**C/C++**  >  **Command Line** .

1. Zmodyfikuj właściwość **Opcje dodatkowe** , aby uwzględnić **`cgthreadsN`** , gdzie *`N`* ma wartość od 1 do 8, a następnie wybierz **przycisk OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
