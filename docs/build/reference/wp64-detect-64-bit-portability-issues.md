---
title: /Wp64 (Wykrywaj problemy związane z przenośnością w programowaniu 64-bitowym)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: e5c30ac9096094948a83195f5b3990794c421685
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335888"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Wykrywaj problemy związane z przenośnością w programowaniu 64-bitowym)

Ta opcja kompilatora jest przestarzała. W wersjach programu Visual Studio przed programem Visual Studio 2013 wykrywa problemy z przenoszeniem 64-bitowe na typy, które są również oznaczone [__w64](../../cpp/w64.md) słowa kluczowego.

## <a name="syntax"></a>Składnia

```
/Wp64
```

## <a name="remarks"></a>Uwagi

Domyślnie w wersjach programu Visual Studio przed programem Visual Studio 2013 opcja kompilatora **/Wp64** jest wyłączona w kompilatorze MSVC, który tworzy 32-bitowy kod x86, a następnie w kompilatorze MSVC, który tworzy 64-bitowy kod x64.

> [!IMPORTANT]
> Opcja kompilatora [/Wp64](wp64-detect-64-bit-portability-issues.md) i [__w64](../../cpp/w64.md) słowo kluczowe są przestarzałe w programie Visual Studio 2010 i Visual Studio 2012 i nie są obsługiwane począwszy od programu Visual Studio 2013. Jeśli przekonwertujesz projekt, który używa tego przełącznika, przełącznik nie zostanie zmigrowany podczas konwersji. Aby użyć tej opcji w programie Visual Studio 2010 lub Visual Studio 2012, należy wpisać przełącznik kompilatora w obszarze **Opcje dodatkowe** w sekcji **Wiersz polecenia** właściwości projektu. Jeśli używasz opcji kompilatora **/Wp64** w wierszu polecenia, kompilator wydaje ostrzeżenie wiersza polecenia D9002. Zamiast używać tej opcji i słowa kluczowego do wykrywania problemów z przenośnością 64-bitowych, należy użyć kompilatora MSVC, który jest przeznaczony dla platformy 64-bitowej i określić opcję [/W4.](compiler-option-warning-level.md) Aby uzyskać więcej informacji, zobacz [Konfigurowanie projektów języka C++ dla 64-bitowych obiektów docelowych x64](../configuring-programs-for-64-bit-visual-cpp.md).

Zmienne następujących typów są testowane w 32-bitowym systemie operacyjnym tak, jakby były używane w 64-bitowym systemie operacyjnym:

- int

- long

- pointer

Jeśli regularnie kompilujesz aplikację przy użyciu kompilatora, który tworzy 64-bitowy kod x64, możesz po prostu wyłączyć **/Wp64** w kompilacjach 32-bitowych, ponieważ kompilator 64-bitowy wykryje wszystkie problemy. Aby uzyskać więcej informacji na temat kierowania na 64-bitowy system operacyjny Windows, zobacz [Konfigurowanie projektów języka C++ dla 64-bitowych obiektów docelowych x64](../configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu.

   Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Wiersz polecenia.**

1. Zmodyfikuj pole **Opcje dodatkowe,** aby uwzględnić **/Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Konfigurowanie projektów języka C++ dla 64-bitowych obiektów docelowych x64](../configuring-programs-for-64-bit-visual-cpp.md)
