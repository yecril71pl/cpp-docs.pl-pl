---
title: /Oy (Pominięcie wskaźnika ramki)
ms.date: 11/19/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
ms.openlocfilehash: 343b0e026c2932e97d4a8d4472ba2035d6302661
ms.sourcegitcommit: 3da2cb3ec85e77ddfd4d2a55edb133d580ce4f18
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52330393"
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Pominięcie wskaźnika ramki)

Pomija tworzenie wskaźników ramek na stosie wywołań.

## <a name="syntax"></a>Składnia

> /Oy [-]

## <a name="remarks"></a>Uwagi

Ta opcja przyspiesza wywołania funkcji, ponieważ nie trzeba definiować i usuwać żadnych wskaźników ramek. Uwalnia jeden lub więcej rejestrów do użytku ogólnego.

**/Oy** umożliwia pominięcie wskaźnika ramki i **/Oy-** wyłącza pominięcie. W x64 kompilatorów **/Oy** i **/Oy-** nie są dostępne.

Jeśli kod wymaga adresowania opartego na ramce, możesz określić **/Oy-** po opcji **ox** lub użyć [zoptymalizować](../../preprocessor/optimize.md) za pomocą "**y**"i **poza** argumenty, aby uzyskać maksymalną optymalizację z systemem adresowania opartym na ramki. Kompilator wykrywa większość sytuacji, w których wymagane jest adresowanie oparte na ramki (na przykład z `_alloca` i `setjmp` funkcje i obsługą wyjątków strukturalnych).

[OX (Włącz większość optymalizacji szybkości)](../../build/reference/ox-full-optimization.md) i [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) opcje oznaczają **/Oy**. Określanie **/Oy-** po **ox**, **/O1**, lub **/O2** wyłącza opcję **/Oy**, czy jest ono jawnych ani dorozumianych.

**/Oy** kompilatora opcji sprawia, że debuger ma trudniejsze ponieważ kompilator pomija informacje o wskaźnikach ramek. Jeśli określisz kompilatorze opcję debugowania ([/z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), firma Microsoft zaleca, aby określić **/Oy-** opcji po wszelkich innych opcjach optymalizacji w kompilatorze.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **optymalizacji** stronę właściwości.

1. Modyfikowanie **Pomiń wskaźniki ramki** właściwości. Właściwość ta dodaje lub usuwa tylko **/Oy** opcji. Jeśli chcesz dodać **/Oy-** wybierz **wiersza polecenia** właściwości strony i zmodyfikuj **dodatkowe opcje**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Zobacz też

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)<br/>
