---
title: /U, /u (Usuń definicje symboli)
description: Użyj opcji/U i/u kompilatora Microsoft C/C++, aby nie definiować symboli preprocesora.
ms.date: 09/03/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: 78effabba2fa72e5ab7f2dfc6ef91f22383b063f
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609199"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Usuń definicje symboli)

**`/U`** Opcja kompilatora dedefiniuje określony symbol preprocesora. **`/u`** Opcja kompilatora umożliwia oddefiniowanie symboli specyficznych dla firmy Microsoft, które definiuje kompilator.

## <a name="syntax"></a>Składnia

> **`/U`**\[ ] —*symbol*\
> **`/u`**

## <a name="arguments"></a>Argumenty

* — symbol*<br/>
Symbol preprocesora, który ma zostać niezdefiniowany.

## <a name="remarks"></a>Uwagi

Żadna z **`/U`** opcji i nie **`/u`** może definiować symbolu utworzonego za pomocą **`#define`** dyrektywy.

**`/U`** Opcja może oddefiniować symbol, który został wcześniej zdefiniowany przy użyciu **`/D`** opcji.

Domyślnie kompilator może definiować dużą liczbę symboli specyficznych dla firmy Microsoft. Poniżej przedstawiono kilka typowych:

| Symbol | Funkcja |
|--|--|
| `_CHAR_UNSIGNED` | Domyślny typ char jest niepodpisany. Zdefiniowane, gdy [`/J`](j-default-char-type-is-unsigned.md) opcja jest określona. |
| `_CPPRTTI` | Zdefiniowane dla kodu skompilowanego z [`/GR`](gr-enable-run-time-type-information.md) opcją. |
| `_CPPUNWIND` | Zdefiniowane dla kodu skompilowanego z [`/EHsc`](eh-exception-handling-model.md) opcją. |
| `_DLL` | Zdefiniowane, gdy [`/MD`](md-mt-ld-use-run-time-library.md) opcja jest określona. |
| `_M_IX86` | Domyślnie zdefiniowane do 600 dla obiektów docelowych x86. |
| `_MSC_VER` | Zdefiniowane jako unikatowa wartość całkowita dla każdej wersji kompilatora. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md). |
| `_WIN32` | Zdefiniowane dla aplikacji WIN32. Zawsze zdefiniowane. |
| `_MT` | Zdefiniowane, gdy [`/MD`](md-mt-ld-use-run-time-library.md) [`/MT`](md-mt-ld-use-run-time-library.md) jest określona opcja or. |

Aby zapoznać się z pełną listą wstępnie zdefiniowanych makr specyficznych dla firmy Microsoft, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja**  >  **C/C++**  >  **zaawansowana** C/C++.

1. Zmodyfikuj **Definicje preprocesora** lub Usuń **wszystkie właściwości definicji preprocesora** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> lub <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A> .

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[**`/J`** (Domyślny typ char nie jest podpisany)](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`** (Włącz informacje typu run-time)](gr-enable-run-time-type-information.md)<br/>
[**`/EH`** (Model obsługi wyjątków)](eh-exception-handling-model.md)<br/>
[**`/MD`**, **`/MT`** , **`/LD`** (Użyj biblioteki wykonawczej)](md-mt-ld-use-run-time-library.md)
