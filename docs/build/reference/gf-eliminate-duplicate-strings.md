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
ms.openlocfilehash: 2f2bec446fcec522857b4c05a34311e6c26c9b75
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812320"
---
# <a name="gf-eliminate-duplicate-strings"></a>/GF (Eliminowanie ciągów zduplikowanych)

Umożliwia kompilatorowi tworzenie pojedynczej kopii identycznych ciągów w obrazie programu i w pamięci podczas wykonywania. Jest to optymalizacją nazywaną *stringów* , można utworzyć mniejszymi programami.

## <a name="syntax"></a>Składnia

```
/GF
```

## <a name="remarks"></a>Uwagi

Jeśli używasz **/GF**, system operacyjny nie zamienić ciąg część pamięci i mogą odczytywać ciągi kopię z pliku obrazu.

**/GF** pul ciągi jako tylko do odczytu. Jeśli spróbujesz zmodyfikować ciągi w **/GF**, występuje błąd aplikacji.

Buforowanie ciągów umożliwia co miały jako wielu wskaźników do buforów wiele do wielu wskaźników do pojedynczego buforu. W poniższym kodzie `s` i `t` są inicjowane za pomocą tego samego ciągu. Buforowanie ciągu powoduje, że ich wskaż tej samej pamięci:

```
char *s = "This is a character buffer";
char *t = "This is a character buffer";
```

> [!NOTE]
>  [/Zi](z7-zi-zi-debug-information-format.md) , używane do edycji i kontynuowania oraz powoduje **/GF** opcji.

> [!NOTE]
>  **/GF** — opcja kompilatora tworzy adresowalnych sekcji każdy unikatowy ciąg. I domyślnie plik obiektu może zawierać maksymalnie 65 536 adresowalnych sekcji. Jeśli program zawiera więcej niż 65536 ciągów, użyj [/bigobj](bigobj-increase-number-of-sections-in-dot-obj-file.md) opcję kompilatora, aby utworzyć więcej sekcji.

**/GF** jest w działa, gdy [/O1](o1-o2-minimize-size-maximize-speed.md) lub **/O2** jest używany.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **generowania kodu** stronę właściwości.

1. Modyfikowanie **Włącz buforowanie ciągów** właściwości.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
