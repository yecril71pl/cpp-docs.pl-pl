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
ms.openlocfilehash: 39b03b0faf975caba8c5a287c88afcdf53f7a71f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378236"
---
# <a name="yd-place-debug-information-in-object-file"></a>/Yd (Umieść informacje o debugowaniu w pliku obiektu)
Pełne informacje we wszystkich plikach obiektu debugowania nadać tempo utworzone na podstawie pliku prekompilowanego nagłówka (.pch), gdy jest używany z [/Yc](../../build/reference/yc-create-precompiled-header-file.md) i [/z7](../../build/reference/z7-zi-zi-debug-information-format.md) opcje. Przestarzałe.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Yd  
```  
  
## <a name="remarks"></a>Uwagi  
 **/YD** jest przestarzały; [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] teraz obsługuje stosowanie wielu obiektów zapisywania do pliku .pdb pojedynczego **/zi** zamiast tego. Listę opcji kompilatora przestarzałe, zobacz **uznane za przestarzałe i usunąć — opcje kompilatora** w [kompilatora opcje rozbiciu na kategorie](../../build/reference/compiler-options-listed-by-category.md).  
  
 O ile nie trzeba rozpowszechniać biblioteki zawierające informacje debugowania, użyj [/zi](../../build/reference/z7-zi-zi-debug-information-format.md) opcji zamiast **/z7** i **/Yd**.  
  
 Przechowywanie pełne informacje o debugowaniu w każdym pliku .obj jest konieczne tylko dystrybucji bibliotek, które zawierają informacje o debugowaniu. Spowalnia kompilacji, a wymaga dużo wolnego miejsca. Gdy **/Yc** i **/z7** są używane bez **/Yd**, kompilator przechowuje typowych informacji o debugowaniu w pliku .obj pierwszy utworzone na podstawie pliku .pch. Kompilator nie wstawić tych informacji do plików .obj następnie utworzone na podstawie pliku .pch; wstawia odsyłacze do informacji. Niezależnie od tego, ile plików .obj użyć pliku .pch tylko jeden plik .obj zawiera typowe informacje debugowania.  
  
 Mimo że domyślne zachowanie powoduje to szybsze tworzenie razy i zmniejsza wymagania miejsca na dysku, jest niepożądanych niewielkie zmiany wymaga odbudowanie pliku .obj zawierającego typowych informacji debugowania. W takim przypadku kompilator ponownie wszystkie pliki .obj zawierające odsyłacze do oryginalnego pliku .obj. Ponadto jeżeli wspólnej pliku .pch jest używany przez różnych projektów, zależność od odsyłacze do pliku .obj pojedynczego jest trudne.  
  
 Aby uzyskać więcej informacji o prekompilowanych nagłówków zobacz:  
  
-   [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)  
  
-   [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Kliknij przycisk **C/C++** folderu.  
  
3.  Kliknij przycisk **wiersza polecenia** strony właściwości.  
  
4.  Typ opcji kompilatora w **dodatkowe opcje** pole.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="examples"></a>Przykłady  
 Załóżmy, że użytkownik ma dwa podstawowe pliki F.cpp i G.cpp każdego zawierające te **#include** instrukcji:  
  
```  
#include "windows.h"  
#include "etc.h"  
```  
  
 Poniższe polecenie tworzy prekompilowanego nagłówka pliku ETC.pch i pliku obiektu F.obj:  
  
```  
CL /YcETC.H /Z7 F.CPP  
```  
  
 Plik obiektu F.obj zawiera typ i informacji o symbolach dla WINDOWS.h i ETC.h (i inne pliki nagłówków, które obejmują one). Teraz można prekompilowany nagłówek ETC.pch skompiluj plik źródłowy G.cpp:  
  
```  
CL /YuETC.H /Z7 G.CPP  
```  
  
 Plik obiektu G.obj nie zawiera informacji o debugowaniu dla prekompilowanego nagłówka, ale po prostu odwołuje się do tych informacji w pliku F.obj. Należy pamiętać, że należy powiązać z plikiem F.obj.  
  
 Jeśli Twoje prekompilowany nagłówek nie został skompilowany z **/z7**, możesz nadal używać go w nowszej kompilacji za pomocą **/z7**. Informacje o debugowaniu znajduje się w bieżącym pliku obiektu i symboli lokalnych dla funkcji i typów zdefiniowanych we prekompilowanym nagłówku nie są dostępne do debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)