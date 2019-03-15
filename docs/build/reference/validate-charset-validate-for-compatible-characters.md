---
title: / Validate-Charset (Zweryfikuj zgodność znaków)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 30c818bcb64c2f2ee57c05a4870e7d30afe98cfe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810071"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/ Validate-Charset (Zweryfikuj zgodność znaków)

Sprawdza, czy tekst plik źródłowy zawiera tylko znaki stałego jako UTF-8.

## <a name="syntax"></a>Składnia

```
/validate-charset[-]
```

## <a name="remarks"></a>Uwagi

Możesz użyć **/Validate-Charset** opcję, aby zweryfikować, że kod źródłowy zawiera tylko do zestawu znaków, które mogą być reprezentowane w znaków źródła i zestaw znaków wykonania. Ten test jest włączana automatycznie po określeniu **/Source-Charset**, **/Execution-Charset**, lub **/UTF-8** opcje kompilatora. Można jawnie wyłączyć ten test, określając **/ validate-charset —** opcji.

Domyślnie program Visual Studio wykrywa znacznika kolejności bajtów, aby określić, czy plik źródłowy jest w formacie zakodowanym Unicode, na przykład, UTF-16 lub UTF-8. Jeśli zostanie znaleziony Brak znacznika kolejności bajtów, zakłada się plik źródłowy jest zakodowane przy użyciu bieżącej stronie kodowej użytkownika, chyba że strona kodowa zostali zdefiniowani za pomocą **/UTF-8** lub **/Source-Charset** opcji. Program Visual Studio umożliwia zapisywanie kodu źródłowego języka C++ za pomocą jednej z kilku kodowania znaków. Aby uzyskać informacji na temat zestawów znaków źródła i wykonania, zobacz [zestawy znaków](../../cpp/character-sets.md) w dokumentacji języka. Aby uzyskać listę obsługiwanych identyfikatorami stronę kodu i nazwy zestawu znaków, zobacz [kodu strony identyfikatory](/windows/desktop/Intl/code-page-identifiers).

Visual Studio używa UTF-8 jako wewnętrzne kodowanie znaków podczas konwersji między zestaw znaków źródła i wykonania zestawu znaków. Jeśli znak w pliku źródłowym, nie można przedstawić w zestawie znaków wykonywania, konwersja UTF-8 zastępuje znak zapytania '?' znaków. **/Validate-Charset** opcja powoduje, że kompilacji zgłosić ostrzeżenie, jeśli ten problem wystąpi.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Rozwiń **właściwości konfiguracji**, **C/C++**, **wiersza polecenia** folderu.

1. W **dodatkowe opcje**, Dodaj **/Validate-Charset** opcji, a następnie określ preferowany kodowania.

1. Wybierz **OK** Aby zapisać zmiany.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)<br/>
[/ Execution-Charset (Ustaw zestaw znaków wykonywania)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (Ustaw źródłowy zestaw znaków)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (Ustaw źródłowy i wykonywalny zestaw znaków na UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
