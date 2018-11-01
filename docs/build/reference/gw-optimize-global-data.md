---
title: /Gw (Optymalizuj dane globalne)
ms.date: 11/04/2016
f1_keywords:
- /Gw
helpviewer_keywords:
- /Gw compiler option [C++]
- -Gw compiler option [C++]
ms.assetid: 6f90f4e9-5eb8-4c47-886e-631278a5a4a9
ms.openlocfilehash: 406b1577b77f056e18753db10bae5675febe879e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506694"
---
# <a name="gw-optimize-global-data"></a>/Gw (Optymalizuj dane globalne)

Pakiet danych globalnych w sekcjach COMDAT optymalizacji.

## <a name="syntax"></a>Składnia

```
/Gw[-]
```

## <a name="remarks"></a>Uwagi

**/Gw** opcji powoduje, że kompilator pakiet danych globalnych w poszczególnych sekcjach COMDAT. Domyślnie **/Gw** jest wyłączona i musi być jawnie włączone. Aby wyłączyć go jawnie, użyj **/Gw-**. Gdy oba **/Gw** i [/GL](../../build/reference/gl-whole-program-optimization.md) są włączone, konsolidator używa optymalizacji całego programu do porównywania sekcje COMDAT na wiele plików obiektu, aby wykluczyć nieużywanych danych globalnych lub scalania identyczne tylko do odczytu danych globalnych. To znacznie zmniejszyć rozmiar wynikowego pliku binarnego pliku wykonywalnego.

Gdy kompilujesz i łączysz oddzielnie, można użyć [/OPT: REF](../../build/reference/opt-optimizations.md) — opcja konsolidatora do wykluczenia z pliku wykonywalnego, nieużywane dane globalne w plikach obiektowych skompilowany przy użyciu **/Gw** opcji.

Można również użyć [/OPT: ICF](../../build/reference/opt-optimizations.md) i [opcję/LTCG](../../build/reference/ltcg-link-time-code-generation.md) opcje konsolidatora ze sobą w celu scalenia w pliku wykonywalnym, wszystkie identyczne tylko do odczytu danych globalnych na wiele plików obiektu skompilowanego z **/Gw** opcji.

Aby uzyskać więcej informacji, zobacz [Przedstawiamy /Gw przełącznika kompilatora](http://blogs.msdn.com/b/vcblog/archive/2013/09/11/introducing-gw-compiler-switch.aspx) na blogu zespołu Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Wybierz **C/C++** folderu.

1. Wybierz **wiersza polecenia** stronę właściwości.

1. Modyfikowanie **dodatkowe opcje** właściwości do uwzględnienia **/Gw** , a następnie wybierz **OK**.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)