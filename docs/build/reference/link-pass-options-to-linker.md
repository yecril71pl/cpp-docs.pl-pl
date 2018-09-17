---
title: -link (przepuść opcje do konsolidatora) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /link
dev_langs:
- C++
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 663407e4948ebc4e3c0a1676c44e8d2b4bd53fcc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704122"
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