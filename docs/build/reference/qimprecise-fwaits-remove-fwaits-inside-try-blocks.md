---
title: -Qimprecise_fwaits (usuwanie fwaits wewnątrz bloków Try) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Qimprecise_fwaits
dev_langs:
- C++
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 98dc9416ecee69bca285ff54d6321144c4a3fd02
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724428"
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

## <a name="see-also"></a>Zobacz też

[/Q opcje (operacje na niskim poziomie)](../../build/reference/q-options-low-level-operations.md)
[opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)