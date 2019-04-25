---
title: /J (Domyślny typ char nie jest podpisany)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.DefaultCharIsUnsigned
- VC.Project.VCCLWCECompilerTool.DefaultCharIsUnsigned
- /j
helpviewer_keywords:
- defaults, char type
- char data type
- -J compiler option [C++]
- /J compiler option [C++]
- J compiler option [C++]
- default char type is unsigned
ms.assetid: 50973667-6638-491e-9c41-bff73acae19f
ms.openlocfilehash: ed296d339949814dbd796bb5d8e23a406be71c69
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269404"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Domyślny typ char nie jest podpisany)

Zmienia domyślny `char` typ z `signed char` do `unsigned char`i `char` typu jest rozszerzony zero, gdy zostanie rozszerzone do `int` typu.

## <a name="syntax"></a>Składnia

```
/J
```

## <a name="remarks"></a>Uwagi

Jeśli `char` wartość jest jawnie zadeklarowana jako `signed`, **/j.** opcji nie ma wpływu na jego, a wartość jest rozszerzona o znak, gdy zostanie rozszerzone do `int` typu.

**/J.** opcja definiuje `_CHAR_UNSIGNED`, który jest używany z `#ifndef` w pliku LIMITS.h, aby zdefiniować zakres domyślnych `char` typu.

ANSI C i C++ nie wymagają określonej implementacji `char` typu. Ta opcja jest przydatna podczas pracy z danymi znaku, który ostatecznie zostanie zamieniona na język inny niż angielski.

> [!NOTE]
>  Jeśli używasz tej opcji kompilatora przy użyciu ATL/MFC, może być wygenerowany błąd. Mimo że można wyłączyć ten błąd, definiując `_ATL_ALLOW_CHAR_UNSIGNED`, to rozwiązanie nie jest obsługiwana i może czasem nie działać.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, a następnie wybierz **właściwości**.

1. W projekcie **stron właściwości** okno dialogowe, w okienku po lewej stronie w obszarze **właściwości konfiguracji**, rozwiń węzeł **C/C++** , a następnie wybierz **wiersza polecenia**.

1. W **dodatkowe opcje** okienku określ **/j.** — opcja kompilatora.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)
