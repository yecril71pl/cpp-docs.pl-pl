---
title: /Qimprecise_fwaits (Usuwanie fwaits wewnątrz bloków Try)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 424feda66f6925cb305256249101ea4013e3090f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232680"
---
# <a name="qimprecise_fwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Usuwanie fwaits wewnątrz bloków Try)

Usuwa `fwait` polecenia wewnętrzne do **`try`** bloków, gdy jest używana opcja kompilatora [/FP: except](fp-specify-floating-point-behavior.md) .

## <a name="syntax"></a>Składnia

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Uwagi

Ta opcja nie działa, jeśli nie określono również **/FP: except** . W przypadku określenia opcji **/FP: except** kompilator wstawi `fwait` polecenie wokół każdego wiersza kodu w **`try`** bloku. W ten sposób kompilator może zidentyfikować konkretny wiersz kodu, który generuje wyjątek. **/Qimprecise_fwaits** usuwa `fwait` instrukcje wewnętrzne, pozostawiając tylko oczekiwania wokół **`try`** bloku. Poprawia to wydajność, ale kompilator będzie mógł tylko powiedzieć **`try`** , który blok powoduje wyjątek, a nie wiersz.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij folder **C/C++** .

1. Kliknij stronę właściwości **wiersza polecenia** .

1. Wpisz opcję kompilatora w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q opcje (operacje na niskim poziomie)](q-options-low-level-operations.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
