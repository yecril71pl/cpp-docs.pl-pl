---
title: -F (Ustaw rozmiar stosu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 244fea4b776f0713b6fb2281563e39d27a910a2d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704258"
---
# <a name="f-set-stack-size"></a>/F (Ustaw rozmiar stosu)

Ustawia rozmiar stosu w bajtach.

## <a name="syntax"></a>Składnia

> **/F** *numer*

## <a name="arguments"></a>Argumenty

*Numer*<br/>
Rozmiar stosu w bajtach.

## <a name="remarks"></a>Uwagi

Bez tej opcji rozmiaru stosu wartość domyślna to 1 MB. *Numer* argument może być dziesiętnych lub notacji języka C. Argument może wynosić od 1 do wielkości maksymalnej stosu zaakceptowane przez konsolidator. Konsolidator zaokrągla w górę określoną wartość do najbliższej 4 bajty. Odstęp między **/F** i *numer* jest opcjonalne.

Może być konieczne zwiększenie rozmiaru stosu, jeśli program pobiera komunikaty przepełnienia stosu.

Można również ustawić rozmiar stosu:

- Za pomocą **/STACK** — opcja konsolidatora. Aby uzyskać więcej informacji, zobacz [/STACK](../../build/reference/stack.md).

- Za pomocą polecenia EDITBIN w pliku .exe. Aby uzyskać więcej informacji, zobacz [odwołanie EDITBIN](../../build/reference/editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)