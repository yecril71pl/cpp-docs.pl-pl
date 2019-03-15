---
title: /Qfast_transcendentals (Wymuszaj fast transcendentals)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 383a915721d627367ca2ca035957df947996bbe2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818352"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Wymuszaj fast transcendentals)

generuje kod wbudowanej funkcji przestępne.

## <a name="syntax"></a>Składnia

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilator wymusza przestępna funkcje są konwertowane na wbudowany kod w celu zwiększenia szybkości wykonywania. Ta opcja obowiązuje tylko wtedy, gdy powiązany z **/FP: z wyjątkiem** lub **/FP: precise**. Generowanie kodu wbudowanego przestępna funkcji jest już zachowanie domyślne w obszarze **Fast**.

Ta opcja jest niezgodna z **/FP: strict**. Zobacz [/FP (określenie zachowania zmiennopozycyjna)](fp-specify-floating-point-behavior.md) Aby uzyskać więcej informacji na temat liczb zmiennoprzecinkowych opcje kompilatora punktu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
