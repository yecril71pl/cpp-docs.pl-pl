---
title: /Qimprecise_fwaits (Usuwanie fwaits wewnątrz bloków Try)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 3f2a0e6bc28fb812e087a689716be6119640ffca
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422146"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Usuwanie fwaits wewnątrz bloków Try)

Usuwa `fwait` polecenia wewnętrzne `try` blokowana, gdy używasz [/FP: except](../../build/reference/fp-specify-floating-point-behavior.md) — opcja kompilatora.

## <a name="syntax"></a>Składnia

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Uwagi

Ta opcja nie obowiązuje, jeśli **/FP: except** również nie zostanie określony. Jeśli określisz **/FP: except** opcja, kompilator wstawi `fwait` polecenia wokół każdego wiersza kodu w `try` bloku. Dzięki temu kompilator może wskazywać konkretnego wiersza kodu, który powoduje wyjątek. **/ Qimprecise_fwaits** usuwa wewnętrzny `fwait` instrukcje, pozostawiając tylko czeka wokół `try` bloku. Poprawia to wydajność, ale kompilator będzie tylko można powiedzieć, który `try` bloku powoduje, że wyjątek nie która linia.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[/Q Opcje (Operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)
