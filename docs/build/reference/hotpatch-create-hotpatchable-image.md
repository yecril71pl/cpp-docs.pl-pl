---
title: /hotpatch (Utwórz obraz możliwy do poprawiania w trakcie działania)
ms.date: 11/04/2016
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
ms.openlocfilehash: b304edffc024fac084338789134269745111ba00
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581444"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Utwórz obraz możliwy do poprawiania w trakcie działania)

Przygotowuje obraz do poprawki.

## <a name="syntax"></a>Składnia

```
/hotpatch
```

## <a name="remarks"></a>Uwagi

Gdy **/hotpatch** jest używany w zestawieniu, kompilator zapewnia, że pierwsza instrukcja każdej funkcji jest co najmniej dwa bajty, który jest wymagany dla poprawki.

Aby zakończyć przygotowania do hotpatchable obraz po użyciu **/hotpatch** skompilować, należy użyć [/FUNCTIONPADMIN (Utwórz obraz Hotpatchable)](../../build/reference/functionpadmin-create-hotpatchable-image.md) połączyć. Gdy kompilujesz i łączysz obraz za pomocą jednego wywołanie cl.exe, **/hotpatch** oznacza **/functionpadmin**.

Ponieważ instrukcje mają zawsze dwa bajty lub większym na architekturze ARM i dlatego x64 kompilacji jest zawsze traktowany tak, jakby **/hotpatch** została określona, nie trzeba określać **/hotpatch** po Kompiluj dla tych celów; Jednakże nadal należy połączyć przy użyciu **/functionpadmin** do tworzenia obrazów hotpatchable dla nich. **/Hotpatch** kompilacja wpływa na x86 tylko opcji kompilatora.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Dodaj opcję kompilatora **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="guidance"></a>Wskazówki

Aby uzyskać więcej informacji na temat zarządzania aktualizacjami, zobacz "Wytyczne bezpieczeństwa do zarządzania aktualizacjami" w [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)