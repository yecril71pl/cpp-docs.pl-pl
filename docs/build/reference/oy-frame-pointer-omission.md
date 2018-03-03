---
title: "-Oy (pominięcie wskaźnika ramki) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/22/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.OmitFramePointers
- /oy
dev_langs:
- C++
helpviewer_keywords:
- omit frame pointer
- Oy compiler option [C++]
- stack frame pointer compiler option [C++]
- -Oy compiler option [C++]
- frame pointer omission compiler option [C++]
- suppress frame pointer creation
- /Oy compiler option [C++]
ms.assetid: c451da86-5297-4c5a-92bc-561d41379853
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15a760d1a9df383356ead2eb2d1e1b08e8b9ca57
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="oy-frame-pointer-omission"></a>/Oy (Pominięcie wskaźnika ramki)

Pomija tworzenie wskaźników ramek na stosie wywołań.

## <a name="syntax"></a>Składnia

> /Oy [-]

## <a name="remarks"></a>Uwagi

Ta opcja przyspiesza wywołania funkcji, ponieważ nie trzeba definiować i usuwać żadnych wskaźników ramek. Uwalnia jeden lub więcej rejestrów (EBP w procesorach Intel 386 lub nowszych) do przechowywania często używanych zmiennych i wyrażeń podrzędnych.

**/Oy** umożliwia pominięcie wskaźnika ramki i **/Oy-** wyłącza pominięcie. **/Oy** jest dostępna tylko w x86 kompilatory.

Jeśli kod wymaga adresowanie na podstawie EBP, można określić **/Oy-** po **ox** opcji lub użyj [zoptymalizować](../../preprocessor/optimize.md) z "**y**" i **poza** argumentów, aby uzyskać maksymalną optymalizacji o podstawie EBP adresowania. Kompilator wykrywa większości sytuacji, w których jest wymagane na podstawie EBP adresowania (na przykład z `_alloca` i `setjmp` funkcje i obsługa wyjątków strukturalnych).

[OX (Włącz najbardziej prędkości optymalizacji)](../../build/reference/ox-full-optimization.md) i [/O1, / O2 (Minimalizuj rozmiar, Maksymalizuj szybkość)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) opcji pociąga za sobą **/Oy**. Określanie **/Oy-** po **ox**, **/O1**, lub **/O2** opcji wyłącza **/Oy**, czy jest ono jawne lub domniemanych.

**/Oy** sprawia, że opcja kompilatora za pomocą debugera trudniejsza, ponieważ kompilator pomija informacje wskaźnika ramki. Jeśli określono opcję kompilatora debugowania ([/z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)), zaleca się, że podajesz **/Oy-** opcji po innych opcji kompilatora optymalizacji.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **optymalizacji** strony właściwości.

1. Modyfikowanie **Pomiń wskaźniki ramek** właściwości. Ta właściwość dodaje lub usuwa tylko **/Oy** opcji. Jeśli chcesz dodać **/Oy-** kliknij przycisk **wiersza polecenia** i zmodyfikuj **dodatkowe opcje**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>.

## <a name="see-also"></a>Zobacz też

[/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)

[Opcje kompilatora](../../build/reference/compiler-options.md)

[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)