---
title: "-clr (kompilacja języka wspólnego środowiska uruchomieniowego) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /CLR
- VC.Project.VCNMakeTool.CompileAsManaged
- VC.Project.VCCLCompilerTool.CompileAsManaged
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, common language runtime option
- -clr compiler option [C++]
- clr compiler option [C++]
- /clr compiler option [C++]
- Managed Extensions for C++, compiling
- common language runtime, /clr compiler option
ms.assetid: fec5a8c0-40ec-484c-a213-8dec918c1d6c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a754e6c2fd8c709fd0397a2c0f78a7385819c586
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)
Umożliwia aplikacji i składników można używać funkcji z środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
/clr[:options]  
```  
  
## <a name="arguments"></a>Argumenty  
 `options`  
 Co najmniej jeden z następujących przełączników rozdzielaną przecinkami.  
  
 **/clr**  
 Tworzy metadane dla aplikacji. Metadane mogą być używane przez inne aplikacje CLR i pozwala aplikacji używać typów i danych w metadanych innych składników CLR.  
  
 Aby uzyskać więcej informacji, zobacz artykuł  
  
 [Mieszane (natywne i zarządzane) zestawy](../../dotnet/mixed-native-and-managed-assemblies.md) i  
  
 [Porady: Migracja do/CLR](../../dotnet/how-to-migrate-to-clr.md).  
  
 **/clr:pure**  
 / CLR: pure jest przestarzały. Przyszłych wersji kompilatora mogą nie obsługiwać tę opcję. Zaleca się, że portu kod, który musi być czysty MSIL do języka C#.  
  
 **/clr:safe**  
 / CLR: Safe jest przestarzały. Przyszłych wersji kompilatora mogą nie obsługiwać tę opcję. Zaleca się, że portu kod, który musi być bezpieczne MSIL do języka C#. 
  
 **/clr:noAssembly**  
 Określa, że nie można wstawić manifest zestawu do pliku wyjściowego. Domyślnie **noAssembly** opcja nie jest włączone.  
  
 **NoAssembly** opcji jest przestarzały. Użyj [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md) zamiast tego.  
  
 Zarządzane program, który nie ma metadanych zestawu w manifeście nosi nazwę *modułu*. **NoAssembly** opcji można użyć tylko w celu utworzenia modułu. Jeśli skompilować przy użyciu [/c](../../build/reference/c-compile-without-linking.md) i **/clr:noAssembly**, następnie określ [/noassembly](../../build/reference/noassembly-create-a-msil-module.md) opcję w fazie konsolidator, aby utworzyć moduł.  
  
 Przed Visual C++ 2005 **/clr:noAssembly** wymagane **/LD**. **/LD** jest teraz niejawnego po określeniu **/clr:noAssembly**.  
  
 **/clr:initialAppDomain**  
 Włącza [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] aplikację do uruchamiania w wersji 1 środowiska CLR. Jeśli używasz **initialAppDomain**, a następnie może zostać wyświetlony niektóre problemy, które zostały omówione w [USTERKI: AppDomainUnloaded wyjątku, gdy używasz rozszerzenia managed extensions dla składników programu Visual C++](http://go.microsoft.com/fwlink/p/?linkid=169465) w programie Microsoft Witryna sieci Web pomocy technicznej.  
  
 Aplikacja, która ma być kompilowana przy użyciu **initialAppDomain** nie powinna być używana przez aplikację, która używa platformy ASP.NET, ponieważ nie jest obsługiwany w wersji 1 środowiska CLR.  
  
 **/clr:nostdlib**  
 Instruuje kompilator, aby zignorować domyślny katalog \clr. Kompilator generuje błędy w przypadku dołączania wielu wersji biblioteki dll, takich jak System.dll. Ta opcja pozwala określić określonej platformy do użycia podczas kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Kod zarządzany jest kodu, które mogą być kontrolowane i zarządzane przez środowisko CLR. Kod zarządzany mają dostęp do obiektów zarządzanych. Aby uzyskać więcej informacji, zobacz [/CLR ograniczenia](../../build/reference/clr-restrictions.md).  
  
 Aby uzyskać informacje o sposobie tworzenia aplikacji, które Definiowanie oraz stosowanie typy zarządzane, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Aplikacji skompilowanych za pomocą **/CLR** może lub nie może zawierać danych zarządzanych.  
  
 Aby włączyć debugowanie w zarządzanej aplikacji, zobacz [/ASSEMBLYDEBUG (Dodaj DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md).  
  
 Wyłącznie typy CLR zostanie utworzona na stercie zbierane pamięci. Aby uzyskać więcej informacji, zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md). Aby skompilować funkcję do kodu macierzystego, należy użyć `unmanaged` pragma. Aby uzyskać więcej informacji, zobacz [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md).  
  
 Domyślnie **/CLR** nie jest włączone. Gdy **/CLR** , **/ / MD** jest również w obiekcie. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Użyj biblioteki wykonawczej)](../../build/reference/md-mt-ld-use-run-time-library.md). **/ / MD** gwarantuje, że dynamicznie połączony, wielowątkowy wersji procedury obsługi są zaznaczone z plików standardowych nagłówków (.h). Wielowątkowość jest wymagany dla zarządzanych programowania, ponieważ moduł garbage collector środowiska CLR uruchamia finalizatory w wątku pomocniczych.  
  
 Jeśli skompilować przy użyciu **/c**, można określić typu CLR wynikowego pliku wyjściowego z [clrimagetype](../../build/reference/clrimagetype-specify-type-of-clr-image.md).  
  
 **/ CLR** oznacza **/eha**, a nie inne **/EH** opcje są obsługiwane dla **/CLR**. Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md).  
  
 Aby uzyskać informacje o tym, jak można ustalić typu obrazu CLR pliku, zobacz [/CLRHEADER](../../build/reference/clrheader.md).  
  
 Wszystkie moduły przekazany do danego wywołanie konsolidator muszą być skompilowane przy użyciu tej samej biblioteki wykonawczej opcji kompilatora (**/ / MD** lub **/LD**).  
  
 Użyj [/assemblyresource](../../build/reference/assemblyresource-embed-a-managed-resource.md) — opcja konsolidatora do osadzenia zasobu w zestawie. [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/KeyContainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md), i [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) opcje konsolidatora również umożliwiają dostosowanie sposobu tworzenia zestawu.  
  
 Gdy **/CLR** jest używana, `_MANAGED` symbol zdefiniowany jest równa 1. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).  
  
 Zmienne globalne w pliku obiekt natywny są inicjowane pierwszej (w ramach funkcji DllMain, jeśli plik wykonywalny jest biblioteką DLL), a następnie zmienne globalne w sekcji zarządzane są inicjowane (przed uruchomieniem kodu zarządzanego). `#pragma`[init_seg](../../preprocessor/init-seg.md) wpływa tylko na kolejność inicjowania w kategoriach zarządzane i niezarządzane.  
  
## <a name="metadata-and-unnamed-classes"></a>Metadane i nazwy klas  
 Nazwy klas pojawią się w metadanych o nazwie w następujący sposób: `$UnnamedClass$` *crc z bieżącej pliku nazwa-*`$`*indeksu*`$`, gdzie *indeksu*to liczba sekwencyjnych bez nazwy klas w kompilacji. Na przykład następujący przykładowy kod generuje nienazwanej klasy w metadanych.  
  
```  
// clr_unnamed_class.cpp  
// compile by using: /clr /LD  
class {} x;  
```  
  
 Ildasm.exe umożliwia wyświetlanie metadanych.  
  
## <a name="managed-extensions-for-c"></a>rozszerzenia zarządzane dla C++  
 Visual C++ nie obsługuje już **: oldsyntax** opcji. Ta opcja została uznana za przestarzałą w programie Visual Studio 2005. Jest obsługiwana składnia pisaniu kodu zarządzanego w języku C++ C + +/ CLI. Aby uzyskać więcej informacji, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../../windows/component-extensions-for-runtime-platforms.md).  
  
 Jeśli masz kod, który używa rozszerzeń zarządzanych dla języka C++, firma Microsoft zaleca port do użycia C + +/ CLI składni. Aby uzyskać informacje na temat portu kodu, zobacz [C + +/ CLI migracji Elementarz](../../dotnet/cpp-cli-migration-primer.md).  
  
#### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości** otworzyć projektu **strony właściwości** okno dialogowe.  
  
2.  Wybierz **właściwości konfiguracji** folderu.  
  
3.  Na **ogólne** właściwości strony, zmodyfikuj **Obsługa środowisko uruchomieniowe języka wspólnego** właściwości.  
  
    > [!NOTE]
    >  Gdy **/CLR** jest włączone w **strony właściwości** okno dialogowe, właściwości opcji kompilatora, które nie są zgodne z **/CLR** są również ustawiane, co jest wymagane. Na przykład jeśli **/RTC** jest ustawiona, a następnie **/CLR** jest włączona, **/RTC** zostaną wyłączone.  
    >   
    >  Ponadto podczas debugowania **/CLR** aplikacji, ustaw **typ debugera** właściwości **Mixed** lub **zarządzane tylko**. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration).  
  
     Informacje na temat tworzenia modułu, zobacz [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md).  
  
#### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)