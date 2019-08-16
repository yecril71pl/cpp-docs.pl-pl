---
title: /bigobj (Zwiększ ilość sekcji w pliku .Obj)
ms.date: 03/26/2019
f1_keywords:
- /bigobj
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
ms.openlocfilehash: 30c02c72496e3bb91da3b39e1870f1dc5a2c040a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493114"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zwiększ ilość sekcji w pliku .Obj)

**/bigobj** zwiększa liczbę sekcji, które może zawierać plik obiektu.

## <a name="syntax"></a>Składnia

> **/bigobj**

## <a name="remarks"></a>Uwagi

Domyślnie plik obiektu może zawierać maksymalnie 65 279 (prawie 2 ^ 16) sekcji adresowane. Ten limit obowiązuje niezależnie od tego, która platforma docelowa została określona. **/bigobj** zwiększa pojemność adresu do 4 294 967 296 (2 ^ 32).

Większość modułów nigdy nie generuje pliku. obj, który zawiera więcej niż 65 279 sekcji. Jednak kod wygenerowany przez maszynę lub kod, który sprawia, że są duże użycie bibliotek szablonów, mogą wymagać plików. obj, które mogą zawierać więcej sekcji. **/bigobj** jest domyślnie włączona w projektach platforma uniwersalna systemu Windows (platformy UWP), ponieważ kod XAML wygenerowany przez maszynę zawiera dużą liczbę nagłówków. Jeśli wyłączysz tę opcję w projekcie aplikacji platformy UWP, kod może generować błąd kompilatora C1128.

Aby uzyskać informacje na temat formatu pliku. PE-COFF, zobacz [Format PE](/windows/win32/debug/pe-format) w dokumentacji systemu Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [ C++ Ustawianie właściwości kompilatora i Build w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz stronę właściwości **Konfiguracja** > **C/C++**  > **wiersz polecenia** .

1. Wprowadź opcję kompilatora **/bigobj** w polu **dodatkowe opcje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
