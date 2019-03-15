---
title: /Yd (Umieść informacje o debugowaniu w pliku obiektu)
ms.date: 11/04/2016
f1_keywords:
- /yd
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
ms.openlocfilehash: e6719226d28088d10da6c4f0e6caf3bdb78bea27
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57820159"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Umieść informacje o debugowaniu w pliku obiektu)

Pełne informacje we wszystkich plikach obiektu debugowania tępy utworzone na podstawie pliku prekompilowanego pliku nagłówkowego (.pch), gdy jest używane z [/Yc](yc-create-precompiled-header-file.md) i [/z7](z7-zi-zi-debug-information-format.md) opcje. Przestarzałe.

## <a name="syntax"></a>Składnia

```
/Yd
```

## <a name="remarks"></a>Uwagi

**/YD** jest przestarzała; Visual C++ obsługuje teraz wiele obiektów zapis do pliku .pdb w jednym, należy użyć **/zi** zamiast tego. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](compiler-options-listed-by-category.md).

O ile nie trzeba rozpowszechniać biblioteki zawierające informacje debugowania, użyj [/zi](z7-zi-zi-debug-information-format.md) opcji zamiast **/z7** i **/Yd**.

Przechowywanie kompletne informacje debugowania w każdym pliku obj. konieczne jest tylko Dystrybucja bibliotek, które zawierają informacje o debugowaniu. Go spowalnia kompilacji i wymaga dużo wolnego miejsca. Gdy **/Yc** i **/z7** są używane bez **/Yd**, kompilator zapisuje typowych informacji o debugowaniu w pierwszym pliku .obj, utworzonego na podstawie pliku .pch. Kompilator nie wstawić tych informacji do plików .obj, następnie utworzonego na podstawie pliku .pch; wstawia odsyłacze do informacji. Niezależnie od tego, ile plików .obj, użyj pliku .pch tylko jeden plik .obj zawiera wspólne informacje debugowania.

Mimo że domyślne zachowanie powoduje to szybsze czasy kompilacji i zmniejsza zapotrzebowanie miejsca na dysku, jest to niepożądane Jeśli niewielką zmianę wymaga ponowne tworzenie pliku .obj, zawierających wspólne informacje debugowania. W tym przypadku kompilator ponownie wszystkie pliki .obj zawierający odsyłacze do oryginalnego pliku .obj. Ponadto jeśli wspólnego pliku .pch jest używany w różnych projektach, poleganie na odsyłacze do pliku obj pojedynczy jest trudne.

Aby uzyskać więcej informacji na temat wstępnie skompilowanych nagłówków zobacz:

- [/Y (Prekompilowane nagłówki)](y-precompiled-headers.md)

- [Prekompilowane pliki nagłówka](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio

1. Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md).

1. Kliknij przycisk **C/C++** folderu.

1. Kliknij przycisk **wiersza polecenia** stronę właściwości.

1. Wpisz opcje kompilatora w **dodatkowe opcje** pole.

### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Przykłady

Załóżmy, że masz dwa pliki podstawowego F.cpp i G.cpp, zawierających te **#include** instrukcji:

```
#include "windows.h"
#include "etc.h"
```

Następujące polecenie tworzy prekompilowany plik nagłówkowy ETC.pch i plik obiektu F.obj plików:

```
CL /YcETC.H /Z7 F.CPP
```

Plik obiektu F.obj zawiera typ i informacje o symbolach dla WINDOWS.h i ETC.h (i inne pliki nagłówkowe, które obejmują one). Teraz można użyć prekompilowany plik nagłówkowy ETC.pch do kompilowania pliku źródłowego G.cpp:

```
CL /YuETC.H /Z7 G.CPP
```

Plik obiektu G.obj nie zawiera informacje o debugowaniu dla prekompilowanego nagłówka, ale po prostu odwołuje się do tych informacji w pliku F.obj. Należy pamiętać, że należy połączyć z plikiem F.obj.

Jeśli Twoje wstępnie skompilowanego nagłówka nie został skompilowany przy użyciu **/z7**, można nadal używać go w nowszej kompilacji przy użyciu **/z7**. Informacje o debugowaniu znajduje się w bieżącym pliku obiektu i symboli lokalnych dla funkcji i typów zdefiniowanych w prekompilowanego pliku nagłówkowego nie są dostępne do debugera.

## <a name="see-also"></a>Zobacz także

[MSVC Compiler Options](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
