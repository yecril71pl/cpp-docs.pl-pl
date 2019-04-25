---
title: /F (Ustaw rozmiar stosu)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 9db595daa7de7820b594a8515ece7481b4382c98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293098"
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

- Za pomocą **/STACK** — opcja konsolidatora. Aby uzyskać więcej informacji, zobacz [/STACK](stack.md).

- Za pomocą polecenia EDITBIN w pliku .exe. Aby uzyskać więcej informacji, zobacz [odwołanie EDITBIN](editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
