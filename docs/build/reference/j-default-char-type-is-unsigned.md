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
ms.openlocfilehash: 7bcf0f2eb2bef08757250999d0a6696b256fb15c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322197"
---
# <a name="j-default-char-type-is-unsigned"></a>/J (Domyślny typ char nie jest podpisany)

Zmienia typ `char` domyślny `signed char` z `unsigned char`, a `char` typ jest rozszerzony zerem, gdy jest rozszerzany do `int` typu.

## <a name="syntax"></a>Składnia

```
/J
```

## <a name="remarks"></a>Uwagi

Jeśli `char` wartość jest jawnie `signed`zadeklarowana jako , opcja **/J** nie wpływa na nią, a wartość `int` jest rozszerzana na znak, gdy jest rozszerzana do typu.

Opcja **/J** definiuje `_CHAR_UNSIGNED`opcję , `#ifndef` która jest używana w pliku LIMITS.h `char` do definiowania zakresu typu domyślnego.

ANSI C i C++ nie wymagają `char` określonej implementacji typu. Ta opcja jest przydatna podczas pracy z danymi znaków, które ostatecznie zostaną przetłumaczone na język inny niż angielski.

> [!NOTE]
> Jeśli używasz tej opcji kompilatora z ATL/MFC, może zostać wygenerowany błąd. Chociaż można wyłączyć ten błąd, definiując, `_ATL_ALLOW_CHAR_UNSIGNED`to obejście nie jest obsługiwane i nie zawsze może działać.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. W **Eksploratorze rozwiązań**otwórz menu **skrótów**dla projektu, a następnie wybierz polecenie Właściwości .

1. W oknie dialogowym **Strony właściwości** projektu w lewym okienku w obszarze **Właściwości konfiguracji**rozwiń węzeł **C/C++,** a następnie wybierz pozycję **Wiersz polecenia**.

1. W okienku **Opcje dodatkowe** określ opcję kompilatora **/J.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DefaultCharIsUnsigned%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)
