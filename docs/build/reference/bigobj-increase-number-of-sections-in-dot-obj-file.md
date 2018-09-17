---
title: -bigobj (Zwiększ liczbę sekcji w. Plik obj) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /bigobj
dev_langs:
- C++
helpviewer_keywords:
- -bigobj compiler option [C++]
- /bigobj compiler option [C++]
- bigobj compiler option [C++]
ms.assetid: ba94d602-4015-4a8d-86ec-49241ab74c12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5f10456bea8be552df42efe135818ac9c47393fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45721490"
---
# <a name="bigobj-increase-number-of-sections-in-obj-file"></a>/bigobj (Zwiększ ilość sekcji w pliku .Obj)

**/ bigobj** zwiększa liczbę sekcji mogących zawierać pliku obiektu.

## <a name="syntax"></a>Składnia

```
/bigobj
```

## <a name="remarks"></a>Uwagi

Domyślnie plik obiektu może zawierać maksymalnie 65 536 (2 ^ 16) adresowalnych sekcji. Jest to przypadek, niezależnie od tego, która platforma docelowa jest określona. **/ bigobj** powoduje zwiększenie pojemności adresu do 4 294 967 296 (2 ^ 32).

Większość modułów nigdy nie wygeneruje pliku .obj, który zawiera więcej niż 65536 sekcji. Jednakże kod generowany maszynowo lub kod, który sprawia, że intensywne użycie bibliotek szablonu może wymagać plików .obj, które mogą pomieścić więcej sekcji. **/ bigobj** jest włączona domyślnie w projektach platformy uniwersalnej Windows (UWP), ponieważ generowany sprzętowo kod XAML zawiera dużą liczbę nagłówków. Jeśli wyłączysz tę opcję na projekt aplikacji platformy uniwersalnej systemu Windows najprawdopodobniej będzie błąd kompilatora C1128.

Wiązania, które wysłane przed Visual C++ 2005 nie można odczytać plików .obj, które zostały utworzone z **/bigobj**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)