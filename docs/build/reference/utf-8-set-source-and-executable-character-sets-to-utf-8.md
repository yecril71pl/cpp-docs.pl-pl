---
title: /UTF-8 (Ustawianie źródłowych i wykonywalnych zestawów znaków na UTF-8)
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 1ff0f23ad0758642c73b1b35d6d4dd1be20899cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498180"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/UTF-8 (Ustawianie źródłowych i wykonywalnych zestawów znaków na UTF-8)

Określa zestaw znaków źródła i znak wykonywania ustawiony jako UTF-8.

## <a name="syntax"></a>Składnia

```
/utf-8
```

## <a name="remarks"></a>Uwagi

Można użyć opcji **/UTF-8** , aby określić zestaw znaków źródła i wykonania jako zakodowany przy użyciu kodowania UTF-8. Jest równoważne określeniu **określono element/source-charset: UTF-8/Execution-charset: UTF-8** w wierszu polecenia. Każda z tych opcji domyślnie włącza opcję **/Validate-charset** . Aby uzyskać listę obsługiwanych identyfikatorów stron kodowych i nazw zestawów znaków, zobacz [identyfikatory stron kodowych](/windows/win32/Intl/code-page-identifiers).

Domyślnie program Visual Studio wykrywa znacznik kolejności bajtów, aby określić, czy plik źródłowy jest w zakodowanym formacie Unicode, na przykład UTF-16 lub UTF-8. Jeśli nie zostanie znaleziony znacznik kolejności bajtów, zakłada, że plik źródłowy jest zakodowany przy użyciu bieżącej strony kodowej użytkownika, o ile nie określono strony kodowej za pomocą **/UTF-8** lub opcji **określono element/source-charset** . Program Visual Studio umożliwia zapisanie kodu C++ źródłowego przy użyciu dowolnego z kilku kodowań znaków. Aby uzyskać informacje o zestawach znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać więcej informacji, [Zobacz C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń węzeł **Właściwości konfiguracji**, **C/C++** , **wiersz polecenia** .

1. W obszarze **Opcje dodatkowe**Dodaj opcję **/UTF-8** , aby określić preferowane kodowanie.

1. Wybierz **przycisk OK** , aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (Ustaw zestaw znaków wykonywania)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (Ustaw źródłowy zestaw znaków)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (Zweryfikuj zgodność znaków)](validate-charset-validate-for-compatible-characters.md)
