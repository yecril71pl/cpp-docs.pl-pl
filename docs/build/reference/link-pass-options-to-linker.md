---
title: /link (Przepuść opcje do konsolidatora)
ms.date: 11/04/2016
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: dfa39988782a0c5bd121b6e18402d3f6b67a13e9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50574931"
---
# <a name="link-pass-options-to-linker"></a>/link (Przepuść opcje do konsolidatora)

Przekazuje co najmniej jedną opcję konsolidatora do konsolidatora.

## <a name="syntax"></a>Składnia

```
/link linkeroptions
```

## <a name="arguments"></a>Argumenty

*linkeroptions*<br/>
— Opcja konsolidatora lub Opcje przekazywane do konsolidatora.

## <a name="remarks"></a>Uwagi

**/Link** opcji wraz z opcjami konsolidatora muszą występować po dowolnej nazwy plików i opcji CL. Obszar jest wymagany między **/link** i `linkeroptions`. Aby uzyskać więcej informacji, zobacz [Ustawianie opcji konsolidatora](../../build/reference/setting-linker-options.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij stronę właściwości konsolidatora.

1. Zmodyfikuj jedną lub więcej właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Nie można programowo zmienić tę opcję kompilatora.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)