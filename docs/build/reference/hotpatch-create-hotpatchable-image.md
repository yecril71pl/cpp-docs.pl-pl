---
title: /hotpatch (Utwórz obraz możliwy do poprawiania w trakcie działania)
ms.date: 11/12/2018
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: 8830b26b8fdfc3db2aa5fe31a52e6226fd554946
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807484"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Utwórz obraz możliwy do poprawiania w trakcie działania)

Przygotowuje obraz do poprawki.

## <a name="syntax"></a>Składnia

```
/hotpatch
```

## <a name="remarks"></a>Uwagi

Gdy **/hotpatch** jest używany w zestawieniu, kompilator zapewnia, że pierwsza instrukcja każdej funkcji jest co najmniej dwa bajty, który jest wymagany dla poprawki.

Aby zakończyć przygotowania do hotpatchable obraz po użyciu **/hotpatch** skompilować, należy użyć [/FUNCTIONPADMIN (Utwórz obraz Hotpatchable)](functionpadmin-create-hotpatchable-image.md) połączyć. Gdy kompilujesz i łączysz obraz za pomocą jednego wywołanie cl.exe, **/hotpatch** oznacza **/functionpadmin**.

Ponieważ instrukcje mają zawsze dwa bajty lub większym na architekturze ARM i dlatego x64 kompilacji jest zawsze traktowany tak, jakby **/hotpatch** została określona, nie trzeba określać **/hotpatch** po Kompiluj dla tych celów; Jednakże nadal należy połączyć przy użyciu **/functionpadmin** do tworzenia obrazów hotpatchable dla nich. **/Hotpatch** kompilacja wpływa na x86 tylko opcji kompilatora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Dodaj opcję kompilatora **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
