---
title: -Yd (umieść informacje o debugowaniu w pliku obiektu) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yd
dev_langs:
- C++
helpviewer_keywords:
- /Yd compiler option [C++]
- -Yd compiler option [C++]
- debugging [C++], debug information files
- Yd compiler option [C++]
ms.assetid: c5a699fe-65ce-461e-964c-7f5eb2a8320a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 86cb8a42b77cd0a932530455f1125125a9f546d9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42585970"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Umieść informacje o debugowaniu w pliku obiektu)
Pełne informacje we wszystkich plikach obiektu debugowania tępy utworzone na podstawie pliku prekompilowanego pliku nagłówkowego (.pch), gdy jest używane z [/Yc](../../build/reference/yc-create-precompiled-header-file.md) i [/z7](../../build/reference/z7-zi-zi-debug-information-format.md) opcje. Przestarzałe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>Uwagi  
 **/YD** jest przestarzała; Visual C++ obsługuje teraz wiele obiektów zapis do pliku .pdb w jednym, należy użyć **/zi** zamiast tego. Aby uzyskać listę opcji kompilatora przestarzałe zobacz **usunięte opcje kompilatora i uznane za przestarzałe** w [opcje kompilatora wymienione według kategorii](../../build/reference/compiler-options-listed-by-category.md).  
  
 O ile nie trzeba rozpowszechniać biblioteki zawierające informacje debugowania, użyj [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji zamiast **/z7** i **/Yd**.  
  
 Przechowywanie kompletne informacje debugowania w każdym pliku obj. konieczne jest tylko Dystrybucja bibliotek, które zawierają informacje o debugowaniu. Go spowalnia kompilacji i wymaga dużo wolnego miejsca. Gdy **/Yc** i **/z7** są używane bez **/Yd**, kompilator zapisuje typowych informacji o debugowaniu w pierwszym pliku .obj, utworzonego na podstawie pliku .pch. Kompilator nie wstawić tych informacji do plików .obj, następnie utworzonego na podstawie pliku .pch; wstawia odsyłacze do informacji. Niezależnie od tego, ile plików .obj, użyj pliku .pch tylko jeden plik .obj zawiera wspólne informacje debugowania.  
  
 Mimo że domyślne zachowanie powoduje to szybsze czasy kompilacji i zmniejsza zapotrzebowanie miejsca na dysku, jest to niepożądane Jeśli niewielką zmianę wymaga ponowne tworzenie pliku .obj, zawierających wspólne informacje debugowania. W tym przypadku kompilator ponownie wszystkie pliki .obj zawierający odsyłacze do oryginalnego pliku .obj. Ponadto jeśli wspólnego pliku .pch jest używany w różnych projektach, poleganie na odsyłacze do pliku obj pojedynczy jest trudne.  
  
 Aby uzyskać więcej informacji na temat wstępnie skompilowanych nagłówków zobacz:  
  
-   [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)  
  
-   [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** stronę właściwości.  
  
4.  Wpisz opcje kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)