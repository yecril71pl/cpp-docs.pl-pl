---
title: / clr (kompilacja języka wspólnego środowiska uruchomieniowego) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6b0f4660e9221855c93835a0a5ba5e0557178a66
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44109865"
---
# <a name="clr-common-language-runtime-compilation"></a>/clr (Kompilacja środowiska uruchomieniowego języka wspólnego)

Umożliwia aplikacji i składników korzystać z funkcji z środowisko uruchomieniowe języka wspólnego (CLR).

## <a name="syntax"></a>Składnia

> **/ CLR**[**:**_opcje_]

## <a name="arguments"></a>Argumenty

*Opcje*  
Co najmniej jeden z następujących przełączników rozdzielaną przecinkami.

- brak

   Bez żadnych opcji **/CLR** tworzy metadane dla aplikacji. Metadane mogą być używane przez inne aplikacje CLR i pozwala aplikacji używać typów i danych w metadanych innych składników CLR. Aby uzyskać więcej informacji, zobacz [zestawy mieszane (natywne i zarządzane)](../../dotnet/mixed-native-and-managed-assemblies.md) i [porady: Migracja do/CLR](../../dotnet/how-to-migrate-to-clr.md).

- **czyste**

   **/ CLR: pure jest przestarzała**. Przyszłych wersji kompilatora mogą nie obsługiwać tę opcję. Zaleca się, że przeniesiesz kod, który musi być czysty MSIL dla języka C#.

- **Bezpieczne**

   **/ CLR: Safe jest przestarzała**. Przyszłych wersji kompilatora mogą nie obsługiwać tę opcję. Zaleca się, że przeniesiesz kod, który musi być bezpieczne MSIL dla języka C#.

- **noAssembly**

   **/CLR:noAssembly jest przestarzała**. Użyj [/LN (Utwórz moduł MSIL)](../../build/reference/ln-create-msil-module.md) zamiast tego.

   Określa, że nie można wstawić w manifeście zestawu do pliku wyjściowego. Domyślnie **noAssembly** opcja nie jest włączone.

   Zarządzany program, który nie ma metadane zestawu w manifeście jest znany jako *modułu*. **NoAssembly** opcja może służyć wyłącznie w celu utworzenia modułu. Jeśli kompilujesz przy użyciu [/c](../../build/reference/c-compile-without-linking.md) i **/clr:noAssembly**, następnie określ [/noassembly](../../build/reference/noassembly-create-a-msil-module.md) opcję w fazie konsolidator, aby utworzyć moduł.

   Przed Visual C++ 2005 **/clr:noAssembly** wymagane **/LD**. **/LD** teraz jest implikowane przy określeniu **/clr:noAssembly**.

- **initialAppDomain**

   Umożliwia aplikacji Visual C++ do uruchomienia na 1 wersję środowiska CLR.  Aplikacja, która jest kompilowany przy użyciu **initialAppDomain** nie powinny być używane przez aplikację, która używa programu ASP.NET, ponieważ nie jest obsługiwana w wersji 1 środowiska CLR.

- **nostdlib**

   Nakazuje kompilatorowi ignorowanie domyślny katalog \clr. W przypadku dołączania wielu wersji biblioteki DLL, takich jak System.dll, kompilator generuje błędy. Użycie tej opcji pozwala określić określonym środowiskiem do użycia podczas kompilacji.

## <a name="remarks"></a>Uwagi

Kod, który może być kontrolowane i zarządzane przez środowisko CLR jest kod zarządzany. Kod zarządzany dostęp do obiektów zarządzanych. Aby uzyskać więcej informacji, zobacz [/CLR ograniczenia](../../build/reference/clr-restrictions.md).

Aby uzyskać informacje o sposobie tworzenia aplikacji, które Definiowanie oraz stosowanie typami zarządzanymi, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../../windows/component-extensions-for-runtime-platforms.md).

Aplikacja skompilowana przy użyciu **/CLR** może lub nie może zawierać danych zarządzanych.

Aby włączyć debugowanie aplikacji zarządzanej, zobacz [/assemblydebug (Dodaj DebuggableAttribute)](../../build/reference/assemblydebug-add-debuggableattribute.md).

Wyłącznie typy CLR zostaną utworzone na stercie zebranych elementów bezużytecznych. Aby uzyskać więcej informacji, zobacz [klas i struktur](../../windows/classes-and-structs-cpp-component-extensions.md). Aby skompilować funkcję do kodu macierzystego, użyj `unmanaged` pragmy. Aby uzyskać więcej informacji, zobacz [zarządzane, niezarządzane](../../preprocessor/managed-unmanaged.md).

Domyślnie **/CLR** nie jest włączone. Gdy **/CLR** jest aktywna, **/MD** jest również w obiekcie. Aby uzyskać więcej informacji, zobacz [/ / MD, / MT, /LD (Korzystaj z bibliotek wykonawczych)](../../build/reference/md-mt-ld-use-run-time-library.md). **/ MD** gwarantuje, że wybrane są połączone dynamicznie, wielowątkowe wersje procedury czasu wykonywania, przy użyciu plików standardowych nagłówków (.h). Wielowątkowość jest wymagany dla zarządzanych przy użyciu programowania, ponieważ moduł odśmiecania pamięci CLR uruchamia finalizatory pomocniczego wątku.

Jeśli kompilujesz przy użyciu **/c**, można określić typ CLR wynikowej pliku wyjściowego z [/clrimagetype](../../build/reference/clrimagetype-specify-type-of-clr-image.md).

**/ CLR** oznacza **/eha**ani żadnej innej **/EH** opcje są obsługiwane w przypadku **/CLR**. Aby uzyskać więcej informacji, zobacz [/EH (Model obsługi wyjątku)](../../build/reference/eh-exception-handling-model.md).

Aby uzyskać informacji dotyczących sposobu ustalenia typu obrazu CLR pliku, zobacz [/CLRHEADER](../../build/reference/clrheader.md).

Wszystkie moduły przekazane do danego wywołania konsolidatora muszą być skompilowane przy użyciu tych samych opcji kompilatora biblioteki wykonawczej (**/MD** lub **/LD**).

Użyj [linkowany](../../build/reference/assemblyresource-embed-a-managed-resource.md) — opcja konsolidatora do osadzenia zasobu w zestawie. [/ DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md), [/KeyContainer](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md), i [/KeyFile](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) opcje konsolidatora również pozwala na dostosowywanie sposobu tworzenia zestawu.

Gdy **/CLR** jest używany, `_MANAGED` symboli jest zdefiniowana jako 1. Aby uzyskać więcej informacji, zobacz [wstępnie zdefiniowane makra](../../preprocessor/predefined-macros.md).

Zmienne globalne w pliku obiekt natywny są inicjowane pierwszej (w ramach funkcji DllMain, jeśli plik wykonywalny jest biblioteką DLL), a następnie zmienne globalne w sekcji zarządzane są inicjowane (przed uruchomieniem kodu zarządzanego). `#pragma` [init_seg](../../preprocessor/init-seg.md) ma wpływ tylko na kolejności inicjowania w kategoriach zarządzanych i niezarządzanych.

## <a name="metadata-and-unnamed-classes"></a>Bez nazwy klasy i metadanych

Bez nazwy klasy pojawi się w metadanych o nazwie w następujący sposób: `$UnnamedClass$` *crc z bieżącego — nazwa pliku*`$`*indeksu*`$`, gdzie *indeksu*jest sekwencyjne liczba bez nazwy klasy w kompilacji. Na przykład poniższy przykładowy kod generuje nienazwanej klasy w metadanych.

```cpp
// clr_unnamed_class.cpp
// compile by using: /clr /LD
class {} x;
```

Ildasm.exe umożliwia wyświetlanie metadanych.

## <a name="managed-extensions-for-c"></a>rozszerzenia zarządzane dla C++

Visual C++ nie obsługuje już **: oldsyntax** opcji. Ta opcja została zakończona w programie Visual Studio 2005. Obsługiwana składnia pisaniu kodu zarządzanego w języku C++ jest C + +/ interfejsu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Component Extensions dla platform środowiska uruchomieniowego](../../windows/component-extensions-for-runtime-platforms.md).

Jeśli masz kod, który używa zarządzanych rozszerzeń języka C++, firma Microsoft zaleca portu do użycia C + +/ CLI składni. Aby uzyskać informacje na temat sposobu przyłącz kod, zobacz [C + +/ CLI Podręcznik migracji](../../dotnet/cpp-cli-migration-primer.md).

#### <a name="to-set-this-compiler-option-in-visual-studio"></a>Aby ustawić tę opcję kompilatora w programie Visual Studio

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu, a następnie kliknij przycisk **właściwości** otworzyć projektu **stron właściwości** okno dialogowe.

1. Wybierz **właściwości konfiguracji** > **ogólne** stronę właściwości.

1. Modyfikowanie **Obsługa środowiska uruchomieniowego języka wspólnego** właściwości.

   > [!NOTE]
   > Gdy **/CLR** jest włączone w **strony właściwości** okno dialogowe, właściwości opcji kompilatora, które nie są zgodne z **/CLR** również zostaną dopasowane, stosownie do potrzeb. Na przykład jeśli **usunęliśmy** ustawiono i następnie **/CLR** jest włączona, **usunęliśmy** zostaną wyłączone.
   >
   >  Ponadto podczas debugowania **/CLR** aplikacji, ustawić **typ debugera** właściwości **mieszany** lub **zarządzanych tylko**. Aby uzyskać więcej informacji, zobacz [ustawienia projektu dla konfiguracji debugowania języka C++](/visualstudio/debugger/project-settings-for-a-cpp-debug-configuration).

   Aby uzyskać informacje na temat tworzenia modułu, zobacz [/noassembly (Utwórz moduł MSIL)](../../build/reference/noassembly-create-a-msil-module.md).

#### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora

- Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAsManaged%2A>.

## <a name="see-also"></a>Zobacz też

[Opcje kompilatora](../../build/reference/compiler-options.md)   
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)