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
ms.openlocfilehash: d95fed3d9af81d89ac03a52a1e6433786118430e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223840"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Domyślny typ char nie jest podpisany)

Zmienia domyślny **`char`** Typ z **`signed char`** na **`unsigned char`** , a **`char`** Typ to zero-Extended, gdy zostanie rozszerzony do **`int`** typu.

## <a name="syntax"></a>Składnia

```
/J
```

## <a name="remarks"></a>Uwagi

Jeśli **`char`** wartość jest jawnie zadeklarowana jako **`signed`** , opcja **/j** nie wpływa na nią, a wartość jest podwyższenie poziomu, gdy zostanie rozszerzona do **`int`** typu.

Opcja **/j** definiuje `_CHAR_UNSIGNED` , która jest używana z `#ifndef` w pliku Limits. h do definiowania zakresu **`char`** typu domyślnego.

ANSI C i C++ nie wymagają określonej implementacji **`char`** typu. Ta opcja jest przydatna podczas pracy z danymi znakowymi, które ostatecznie zostaną przetłumaczone do języka innego niż angielski.

> [!NOTE]
> W przypadku użycia tej opcji kompilatora z ATL/MFC może zostać wygenerowany błąd. Mimo że ten błąd można wyłączyć przez zdefiniowanie `_ATL_ALLOW_CHAR_UNSIGNED` , to obejście nie jest obsługiwane i może nie zawsze funkcjonować.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, a następnie wybierz polecenie **Właściwości**.

1. W oknie dialogowym **strony właściwości** projektu w lewym okienku w obszarze **Właściwości konfiguracji**rozwiń węzeł **C/C++** , a następnie wybierz pozycję **wiersz polecenia**.

1. W okienku **Opcje dodatkowe** wybierz opcję Opcje kompilatora **/j** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)
