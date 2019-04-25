---
title: / vmb, - vmg (metoda reprezentacji)
ms.date: 11/04/2016
f1_keywords:
- /vmb
- /vmg
helpviewer_keywords:
- vmb compiler option [C++]
- -vmg compiler option [C++]
- vmg compiler option [C++]
- -vmb compiler option [C++]
- /vmb compiler option [C++]
- representation method compiler options [C++]
- /vmg compiler option [C++]
ms.assetid: ecdb391c-7dab-40b1-916b-673d10889fd4
ms.openlocfilehash: eac41de04ec883e7b5acf26596647f912b0b1d20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316746"
---
# <a name="vmb-vmg-representation-method"></a>/vmb, /vmg (Metoda reprezentacji)

Wybierz metodę, której kompilator używa do reprezentowania wskaźników do składowych klasy.

Użyj **/vmb** Jeśli zawsze zdefiniujesz klasę, aby zadeklarować wskaźnik do składowej klasy.

Użyj **/vmg** można zadeklarować wskaźnika do składowej klasy przed zdefiniowaniem klasy. Te wymagania może wystąpić, jeśli zdefiniujesz elementów członkowskich w dwóch różnych klas odwołujące się do siebie nawzajem. Dla tych wzajemnie odwołujący się klas jednej klasy musi odwoływać się przed jego zdefiniowaniem.

## <a name="syntax"></a>Składnia

```
/vmb
/vmg
```

## <a name="remarks"></a>Uwagi

Można również użyć [pointers_to_members](../../preprocessor/pointers-to-members.md) lub [słowa kluczowe dziedziczenia](../../cpp/inheritance-keywords.md) kod w celu określenia reprezentacji wskaźnika.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
