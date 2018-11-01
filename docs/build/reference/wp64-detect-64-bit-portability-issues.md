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
ms.openlocfilehash: 504d7594ab9c636fd3ce7415f3866fb4c0a5aadd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601841"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Wykrywaj problemy związane z przenośnością w programowaniu 64-bitowym)

Ta opcja kompilatora jest przestarzała. W wersjach programu Visual Studio przed Visual Studio 2013 wykrywa to problemów związanych z przenośnością 64-bitowego na typy, które są również oznaczane za pomocą [__w64](../../cpp/w64.md) — słowo kluczowe.

## <a name="syntax"></a>Składnia

```
/Wp64
```

## <a name="remarks"></a>Uwagi

Domyślnie w wersjach programu Visual Studio przed Visual Studio 2013 **/Wp64** — opcja kompilatora jest wyłączona w kompilator Visual C++ kompiluje x86 32-bitowego kodu, i na w przypadku kompilator języka Visual C++, kompilacji 64-bitowy, x64 kodu.

> [!IMPORTANT]
>  [/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) — opcja kompilatora i [__w64](../../cpp/w64.md) — słowo kluczowe są przestarzałe w programie Visual Studio 2010 i Visual Studio 2012, a nie obsługiwane, począwszy od programu Visual Studio 2013. Po skonwertowaniu projektu, który używa tego przełącznika. przełącznik nie zostaną zmigrowane podczas konwersji. Aby użyć tej opcji w programie Visual Studio 2010 lub Visual Studio 2012, należy wpisać przełącznika kompilatora, w obszarze **dodatkowe opcje** w **wiersza polecenia** sekcji we właściwościach projektu. Jeśli używasz **/Wp64** — opcja kompilatora w wierszu polecenia, kompilator generuje D9002 ostrzeżenie wiersza polecenia. Zamiast korzystać z tej opcji i słów kluczowych, wykrywać problemy z przenośnością 64-bitowych, użyj kompilatora Visual C++, który jest przeznaczony dla platformy 64-bitowej i określ [/W4](../../build/reference/compiler-option-warning-level.md) opcji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie Visual C++ x64 64-bitowy, obiekty docelowe](../../build/configuring-programs-for-64-bit-visual-cpp.md).

Następujących typów zmiennych są przetestowane na 32-bitowym systemie operacyjnym, tak, jakby były używane na 64-bitowym systemie operacyjnym:

- int

- long

- pointer

Jeśli kompilujesz regularnie aplikacji za pomocą kompilatora, który tworzy 64-bitowy, x64 kodu, można po prostu wyłączyć **/Wp64** w kompilacjach kodu z 32-bitowych ponieważ 64-bitowy kompilator wykryje wszystkie problemy. Aby uzyskać więcej informacji na temat docelowego Windows 64-bitowego systemu operacyjnego, zobacz [Konfigurowanie Visual C++ x64 64-bitowy, obiekty docelowe](../../build/configuring-programs-for-64-bit-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe.

   Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** pole, aby uwzględnić **/Wp64**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
[Konfigurowanie Visual C++ dla wersji 64-bitowych, platformy docelowe x64](../../build/configuring-programs-for-64-bit-visual-cpp.md)