---
title: /WX (Traktuj ostrzeżenia konsolidatora jak błędy)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: b4b29ed364d39c5f105dded703b8530c08db35e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316304"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (Traktuj ostrzeżenia konsolidatora jak błędy)

```
/WX[:NO]
```

## <a name="remarks"></a>Uwagi

/WX powoduje, że plik wyjściowy nie zostanie wygenerowany, jeśli konsolidator wygeneruje ostrzeżenie.

Jest to podobne do **/WX** dla kompilatora (zobacz [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](compiler-option-warning-level.md) Aby uzyskać więcej informacji). Można jednak określić **/WX** dla kompilacji nie oznacza, że **/WX** również będą obowiązywały do przeprowadzenia w fazie łącze; Musisz jawnie określić **/WX** każdego narzędzia.

Domyślnie **/WX** nie jest włączone. Aby Traktuj ostrzeżenia konsolidatora jako błędy, należy określić **/WX**. **/WX:No** jest taka sama jak brak określenia **/WX**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję konsolidatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje w **dodatkowe opcje** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Aby programowo ustawić tę opcję konsolidatora

1. Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Dokumentacja konsolidatora MSVC](linking.md)<br/>
[Opcje konsolidatora MSVC](linker-options.md)
