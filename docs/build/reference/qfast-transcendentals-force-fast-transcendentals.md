---
title: /Qfast_transcendentals (Wymuszaj fast transcendentals)
ms.date: 11/04/2016
f1_keywords:
- /Qfast_transcendentals
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
ms.openlocfilehash: 512e658cf546e77bff6d58465932d2f830541521
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666131"
---
# <a name="qfasttranscendentals-force-fast-transcendentals"></a>/Qfast_transcendentals (Wymuszaj fast transcendentals)

generuje kod wbudowanej funkcji przestępne.

## <a name="syntax"></a>Składnia

```
/Qfast_transcendentals
```

## <a name="remarks"></a>Uwagi

Ta opcja kompilator wymusza przestępna funkcje są konwertowane na wbudowany kod w celu zwiększenia szybkości wykonywania. Ta opcja obowiązuje tylko wtedy, gdy powiązany z **/FP: z wyjątkiem** lub **/FP: precise**. Generowanie kodu wbudowanego przestępna funkcji jest już zachowanie domyślne w obszarze **Fast**.

Ta opcja jest niezgodna z **/FP: strict**. Zobacz [/FP (określenie zachowania zmiennopozycyjna)](../../build/reference/fp-specify-floating-point-behavior.md) Aby uzyskać więcej informacji na temat liczb zmiennoprzecinkowych opcje kompilatora punktu.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[/Q Opcje (Operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)