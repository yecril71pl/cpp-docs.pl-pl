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
ms.openlocfilehash: 7f40841b82db9f46019ce2a96a61a1a0f622b6d5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813439"
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

**/Link** opcji wraz z opcjami konsolidatora muszą występować po dowolnej nazwy plików i opcji CL. Obszar jest wymagany między **/link** i `linkeroptions`. Aby uzyskać więcej informacji, zobacz [odwołania konsolidatora MSVC](linking.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **konsolidatora** folderu.

1. Kliknij stronę właściwości konsolidatora.

1. Zmodyfikuj jedną lub więcej właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Nie można programowo zmienić tę opcję kompilatora.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
