---
title: /Zo (rozszerzanie zoptymalizowanego debugowania)
ms.date: 11/04/2016
f1_keywords:
- -Zo
- /Zo
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
ms.openlocfilehash: dfc9a0311714d0680316d2d375c92d7902432fcb
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422029"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (rozszerzanie zoptymalizowanego debugowania)

Generuj rozszerzone informacje debugowania dla zoptymalizowanego kodu w kompilacjach nieprzeznaczonych do debugowania.

## <a name="syntax"></a>Składnia

```cpp
/Zo[-]
```

## <a name="remarks"></a>Uwagi

**/Zo** przełącznik kompilator generuje rozszerzone informacje debugowania dla zoptymalizowanego kodu. Optymalizacji może używać rejestrów dla zmiennych lokalnych, zmienianie kolejności kodu, vectorize pętli i wywołania funkcji wbudowanych. Optymalizacje te mogą przesłaniać relacji między kodem źródłowym i skompilowany kod obiektu. **/Zo** przełącznika informuje kompilator, aby wygenerować dodatkowe informacje o debugowaniu dla zmiennych lokalnych i funkcje śródwierszowe. Użyj go, aby wyświetlić zmienne w **Autos**, **lokalne**, i **Obejrzyj** systemu windows, gdy krok po kroku przez zoptymalizowanego kodu w debugerze programu Visual Studio. Umożliwia ona także ślady stosu wyświetlić funkcje śródwierszowe w debugerze WinDBG. Debugowanie kompilacji, które zostały wyłączone optymalizacje ([/Od](../../build/reference/od-disable-debug.md)) nie są dodatkowe informacje debugowania generowane podczas **/Zo** jest określony. Użyj **/Zo** przełącznik, aby debugować konfiguracje wydania z optymalizacją włączona. Aby uzyskać więcej informacji na temat przełączników optymalizacji, zobacz [/O opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md). **/Zo** opcja jest włączona domyślnie w programie Visual Studio, podczas określania informacji o debugowaniu przy użyciu **/zi** lub **/z7**. Określ **/Zo-** jawnie wyłączyć tę opcję kompilatora.

**/Zo** przełącznik jest dostępna, począwszy od programu Visual Studio 2013 Update 3 i zastępuje Nieudokumentowany wcześniej **/d2Zi+** przełącznika.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Aby ustawić /Zo — opcja kompilatora w programie Visual Studio

1. Otwórz **stron właściwości** okno dialogowe dla projektu. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji**, **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia `/Zo` , a następnie wybierz **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/O Opcje (Optymalizuj kod)](../../build/reference/o-options-optimize-code.md)<br/>
[/Z7, /Zi, /ZI (Format informacji o debugowaniu)](../../build/reference/z7-zi-zi-debug-information-format.md)<br/>
[Edytuj i kontynuuj](/visualstudio/debugger/edit-and-continue)
