---
title: -Qfast_transcendentals (Wymuszaj Fast Transcendentals) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qfast_transcendentals
dev_langs:
- C++
helpviewer_keywords:
- /Qfast_transcendentals
- Force Fast Transcendentals
ms.assetid: 4de24bd1-38e6-49d4-9a05-04c9937d24ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d979dc9005921ce1a760b2e61c4519ef852b7f84
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709439"
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

[/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)