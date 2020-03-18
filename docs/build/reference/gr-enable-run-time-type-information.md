---
title: /GR (Włącz informacje typu Run-Time)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.RuntimeTypeInfo
- VC.Project.VCCLCompilerTool.RuntimeTypeInfo
helpviewer_keywords:
- -Gr compiler option [C++]
- Gr compiler option [C++]
- RTTI compiler option
- /Gr compiler option [C++]
- enable run-time type information compiler option [C++]
ms.assetid: d1f9f850-dcec-49fd-96ef-e72d01148906
ms.openlocfilehash: ee1398b2f9ee78c62fb84aa591e77708cd0d9d83
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439586"
---
# <a name="gr-enable-run-time-type-information"></a>/GR (Włącz informacje typu Run-Time)

Dodaje kod do sprawdzania typów obiektów w czasie wykonywania.

## <a name="syntax"></a>Składnia

```
/GR[-]
```

## <a name="remarks"></a>Uwagi

Gdy **/gr** jest włączona, kompilator definiuje makro preprocesora `_CPPRTTI`. Domyślnie **/gr** jest włączone. **/Gr-** wyłącza informacje o typie czasu wykonywania.

Użyj **/gr** , jeśli kompilator nie może statycznie rozpoznać typu obiektu w kodzie. Zwykle potrzebna jest opcja **/gr** , gdy kod używa [operatora dynamic_cast](../../cpp/dynamic-cast-operator.md) lub [typeid](../../cpp/typeid-operator.md). Jednak **/gr** zwiększa rozmiar sekcji obrazu. RDATA. Jeśli kod nie używa **dynamic_cast** lub **typeid**, **/gr-** może generować mniejszy obraz.

Aby uzyskać więcej informacji na temat sprawdzania typu w czasie wykonywania, zobacz [Informacje o typie czasu wykonywania](../../cpp/run-time-type-information.md) w  *C++ dokumentacji języka*.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++**  .

1. Kliknij stronę właściwości **języka** .

1. Zmodyfikuj właściwość **Włącz informacje typu run-time** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeTypeInfo%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
