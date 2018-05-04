---
title: -Yu (Użyj Prekompilowanego pliku nagłówka) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yu
dev_langs:
- C++
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d115017e843e7f03455e1eef2b384b3475a1b798
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (Korzystaj z prekompilowanego pliku nagłówka)
Instruuje kompilator, aby wykorzystywała istniejący plik prekompilowanego nagłówka (.pch) w bieżącej kompilacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Yu[filename]  
```  
  
## <a name="arguments"></a>Argumenty  
 *Nazwa pliku*  
 Nazwa pliku nagłówka, który znajduje się w pliku źródłowym przy użyciu **#include** dyrektywy preprocesora.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa pliku dołączanego musi być takie same dla **/Yc** opcja, która tworzy prekompilowany nagłówek i wszystkie kolejne **/Yu** opcję rezygnacji z używaniem prekompilowanego nagłówka.  
  
 Dla **/Yc**, `filename` określa punkt zatrzymuje które wstępnej kompilacji; kompilator precompiles całego kodu, mimo że `filename` i wynikowy prekompilowanego nagłówka przy użyciu podstawowej nazwy pliku dołączanego i rozszerzenie nazwy z .pch.  
  
 Pliku .pch muszą zostać utworzone przy użyciu **/Yc**.  
  
 Kompilator traktuje wszystkie kod występuje przed pliku .h jako wstępnie skompilowana. Pomija się tylko ponad **#include** dyrektywy skojarzone z plikiem .h używa kod zawarty w pliku .pch, a następnie kompiluje cały kod po `filename`.  
  
 W wierszu polecenia nie może być spacji między **/Yu** i `filename`.  
  
 Po określeniu **/Yu** bez nazwy pliku, program źródłowy musi zawierać [#pragma hdrstop](../../preprocessor/hdrstop.md) pragma, który określa nazwę pliku nagłówka prekompilowanego pliku .pch. W takim przypadku kompilator użyje prekompilowanego nagłówka (pliku .pch) o nazwie [/Fp (nazwa. Plik pch)](../../build/reference/fp-name-dot-pch-file.md). Kompilator przejdzie do lokalizacji tej pragmy przywraca stan skompilowanych z prekompilowanego pliku nagłówkowego określony przez wartość dyrektywy pragma i następnie kompiluje tylko kodu, która pragma. Jeśli **#pragma hdrstop** nie określa nazwę pliku, kompilator szuka pliku o nazwie pochodzące z podstawowej nazwy pliku źródłowego z rozszerzeniem .pch. Można również użyć **/FP** opcję, aby określić .pch inny plik.  
  
 Jeśli określisz **/Yu** opcję bez nazwy pliku i nie można określić **hdrstop** pragma, zostanie wygenerowany komunikat o błędzie i kompilacja zakończy się niepowodzeniem.  
  
 Jeśli **/Yc** `filename` i **/Yu** `filename` opcje są dokonywane na tym samym wierszu polecenia, a oba odwołania dotyczą jednej nazwy pliku **/Yc** `filename` przyjmuje priorytet, do wstępnej kompilacji kodu wszystkich i, w tym wskazanego pliku. Ta funkcja ułatwia zapisywanie pliki reguł programu make.  
  
 Ponieważ .pch — pliki zawierają informacje o środowisku maszyny, a także informacje dotyczące adresów pamięci o programie, należy używać tylko plik pch na komputerze, w której został utworzony.  
  
 Aby uzyskać więcej informacji o prekompilowanych nagłówków zobacz:  
  
-   [/Y (Prekompilowane nagłówki)](../../build/reference/y-precompiled-headers.md)  
  
-   [Tworzenie prekompilowanych plików nagłówka](../../build/reference/creating-precompiled-header-files.md)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Określ [/Yc (Utwórz prekompilowany plik nagłówka)](../../build/reference/yc-create-precompiled-header-file.md) pliku .cpp w projekcie.  
  
2.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
3.  Kliknij przycisk **C/C++** folderu.  
  
4.  Kliknij przycisk **prekompilowanych nagłówków** strony właściwości.  
  
5.  Modyfikowanie **Utwórz/Użyj PCH za pośrednictwem pliku** właściwości lub **Utwórz/Użyj Prekompilowanego nagłówka** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> i <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.  
  
## <a name="examples"></a>Przykłady  
 Jeśli następujący kod:  
  
```  
#include <afxwin.h>   // Include header for class library  
#include "resource.h" // Include resource definitions  
#include "myapp.h"    // Include information specific to this app  
...  
```  
  
 jest skompilowana przy użyciu wiersza polecenia `CL /YuMYAPP.H PROG.CPP`, kompilator nie może przetwarzać trzy zawierają instrukcje, ale kod używa wstępnie skompilowana z MYAPP.pch, co zostanie zapisany czas objętego wstępne przetwarzanie wszystkich trzech plików (i wszystkie pliki, mogą one obejmować).  
  
 Można użyć [/Fp (nazwa. Plik pch)](../../build/reference/fp-name-dot-pch-file.md) opcję z **/Yu** opcję, aby określić nazwę pliku .pch, jeśli nazwa jest inna niż albo argument nazwy pliku do **/Yc** lub podstawowa nazwa pliku źródłowego, jak w następujące:  
  
```  
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP  
```  
  
 To polecenie Określa plik prekompilowany nagłówek o nazwie MYPCH.pch. Kompilator używa jego zawartość w celu przywrócenia stanu prekompilowany wszystkich plików nagłówka do i MYAPP.h włącznie. Kompilator następnie kompiluje kod, który występuje po MYAPP.h **obejmują** instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)