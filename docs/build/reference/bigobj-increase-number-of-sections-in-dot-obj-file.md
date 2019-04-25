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
ms.openlocfilehash: 46399dc0c1ff552b4fc963b686ac6aa6df8b6f71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272978"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zwiększ ilość sekcji w pliku .Obj)

**/ bigobj** zwiększa liczbę sekcji mogących zawierać pliku obiektu.

## <a name="syntax"></a>Składnia

> **/bigobj**

## <a name="remarks"></a>Uwagi

Domyślnie plik obiektu może zawierać maksymalnie 65,279 (prawie 2 ^ 16) adresowalnych sekcji. Ten limit dotyczy, niezależnie od tego, która Docelowa platforma jest określona. **/ bigobj** powoduje zwiększenie pojemności adresu do 4 294 967 296 (2 ^ 32).

Większość modułów nigdy nie Generowanie pliku .obj, który zawiera więcej niż 65,279 sekcje. Jednak generowany sprzętowo kod lub kod, który sprawia, że intensywne użycie bibliotek szablonu może wymagać plików .obj, które mogą pomieścić więcej sekcji. **/ bigobj** jest włączona domyślnie w projektach platformy uniwersalnej Windows (UWP), ponieważ generowany sprzętowo kod XAML zawiera dużą liczbę nagłówków. Jeśli wyłączysz tę opcję na projekt aplikacji platformy uniwersalnej systemu Windows, Twój kod może wygenerować błąd kompilatora C1128.

Aby uzyskać informacje na format plików obiektu PE COFF, zobacz [formatu PE](/windows/desktop/debug/pe-format) w dokumentacji programu Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Wybierz **właściwości konfiguracji** > **C/C++** > **wiersza polecenia** stronę właściwości.

1. Wprowadź **/bigobj** w — opcja kompilatora **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz także

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
