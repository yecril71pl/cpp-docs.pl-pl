---
title: /link (Przepuść opcje do konsolidatora)
ms.date: 03/25/2019
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
ms.openlocfilehash: ef81a6617df811660506c08434f3b65e29155794
ms.sourcegitcommit: 6e4dd21759caaed262a7255735cf8d6e8fb9f4d7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58476841"
---
# <a name="link-pass-options-to-linker"></a>/link (Przepuść opcje do konsolidatora)

Przekazuje co najmniej jedną opcję konsolidatora do konsolidatora.

## <a name="syntax"></a>Składnia

> **/ link** *opcje konsolidatora*

## <a name="arguments"></a>Argumenty

*Opcje konsolidatora*<br/>
— Opcja konsolidatora lub Opcje przekazywane do konsolidatora.

## <a name="remarks"></a>Uwagi

**/Link** opcji wraz z opcjami konsolidatora muszą występować po dowolnej nazwy plików i opcji CL. Obszar jest wymagany między **/link** i `linkeroptions`. Aby uzyskać więcej informacji, zobacz [odwołania konsolidatora MSVC](linking.md).

## <a name="example"></a>Przykład

Ten przykładowy wiersz polecenia kompiluje *hello.cpp* i dołącza go do istniejącego pliku obiektu *there.obj*. Następnie przekazuje dodatkowego **Version** polecenia konsolidatora:

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

IDE zwykle wysyła oddzielnych poleceń, aby skompilować i łączenie kodu. Na stronach właściwości projektu, można ustawić opcje konsolidatora.

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **konsolidatora** folderu.

1. Zmodyfikuj jedną lub więcej właściwości. Wybierz **OK** Aby zapisać zmiany.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Nie można programowo zmienić tę opcję kompilatora.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
