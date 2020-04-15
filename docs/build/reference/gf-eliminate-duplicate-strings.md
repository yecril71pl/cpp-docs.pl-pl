---
title: /GF (Eliminowanie ciągów zduplikowanych)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.StringPooling
- VC.Project.VCCLWCECompilerTool.StringPooling
- /gf
helpviewer_keywords:
- duplicate strings
- Eliminate Duplicate Strings compiler option [C++]
- pooling strings compiler option [C++]
- -GF compiler option [C++]
- /GF compiler option [C++]
- GF compiler option [C++]
- strings [C++], pooling
ms.assetid: bb7b5d1c-8e1f-453b-9298-8fcebf37d16c
ms.openlocfilehash: e0d23004c7b710f51065db52410fbb15b7cca040
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320495"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Eliminowanie ciągów zduplikowanych)

Umożliwia kompilatorowi utworzyć pojedynczą kopię identycznych ciągów w obrazie programu i w pamięci podczas wykonywania. Jest to optymalizacja o nazwie *buforowanie ciągów,* która może tworzyć mniejsze programy.

## <a name="syntax"></a>Składnia

```
/GF
```

## <a name="remarks"></a>Uwagi

Jeśli używasz **/GF**, system operacyjny nie zamienia część ciągu pamięci i może odczytać ciągi z powrotem z pliku obrazu.

**/GF** puluje ciągi jako tylko do odczytu. Jeśli spróbujesz zmodyfikować ciągi w **/GF**, wystąpi błąd aplikacji.

Buforowanie ciągów umożliwia, co było przeznaczone jako wiele wskaźników do wielu buforów, aby być wiele wskaźników do jednego buforu. W poniższym `s` kodzie i `t` są inicjowane z tym samym ciągiem. Buforowanie ciągów powoduje, że wskazują one tę samą pamięć:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
> Opcja [/ZI,](z7-zi-zi-debug-information-format.md) używana do edycji i kontynuowania, automatycznie ustawia opcję **/GF.**

> [!NOTE]
> Opcja kompilatora **/GF** tworzy adresowalną sekcję dla każdego unikatowego ciągu. Domyślnie plik obiektu może zawierać maksymalnie 65 536 adresowalnych sekcji. Jeśli program zawiera więcej niż 65 536 ciągów, użyj opcji kompilatora [/bigobj,](bigobj-increase-number-of-sections-in-dot-obj-file.md) aby utworzyć więcej sekcji.

**/GF** obowiązuje, gdy używany jest [/O1](o1-o2-minimize-size-maximize-speed.md) lub [/O2.](o1-o2-minimize-size-maximize-speed.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz okno dialogowe **Strony właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Ustawianie kompilatora języka C++ i właściwości kompilacji w programie Visual Studio.](../working-with-project-properties.md)

1. Kliknij folder **C/C++.**

1. Kliknij stronę właściwości **Generowanie kodu.**

1. Zmodyfikuj właściwość **Włącz buforowanie ciągów.**

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz: <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
