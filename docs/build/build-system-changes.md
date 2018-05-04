---
title: Zmiany systemu kompilacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- vc.msbuild.changes
dev_langs:
- C++
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 01eb3a38ddaf7cdb1d54061e48680396f16b25e0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="build-system-changes"></a>Zmiany systemu kompilacji
MSBuild system jest używany do tworzenia projektów Visual C++. Jednak w programie Visual Studio 2008 i wcześniejszych wersjach systemu program VCBuild została użyta. Niektóre typy plików i założenia, że program VCBuild nie istnieją lub są reprezentowane inaczej w bieżącym systemie. W tym dokumencie omówiono różnice w systemie kompilacji.  
  
## <a name="vcproj-is-now-vcxproj"></a>.VCPROJ jest teraz .vcxproj  
 Pliki projektu nie są już używane rozszerzenie nazwy pliku .vcproj. Visual Studio automatycznie konwertuje pliki projektu, które zostały utworzone przez wcześniejszą wersją programu Visual C++ do formatu, który jest używany przez bieżący system. Aby uzyskać więcej informacji o sposobie ręcznego uaktualniania projektu, zobacz [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).  
  
 W bieżącej wersji rozszerzenia nazwy pliku dla pliku projektu jest .vcxproj.  
  
## <a name="vsprops-is-now-props"></a>.vsprops — jest teraz .props  
 We wcześniejszych wersjach *arkuszy właściwości projektów* jest plikiem opartych na języku XML, który ma rozszerzenie nazwy pliku .vsprops —. Arkusz właściwości projektu umożliwia określenia przełączniki kompilacji narzędzi, takich jak kompilatora lub konsolidatora i utworzyć makra zdefiniowane przez użytkownika.  
  
 W bieżącej wersji rozszerzenie nazwy pliku arkusza właściwości projektu jest .props.  
  
## <a name="custom-build-rules-and-rules-files"></a>Niestandardowe tworzenie reguł i pliki Rules  
 We wcześniejszych wersjach *pliku reguł* jest plikiem opartych na języku XML, który ma rozszerzenie nazwy pliku rules. Plik reguł pozwala zdefiniować reguły niestandardowej kompilacji i włączyć je do procesu tworzenia projektu Visual C++. Reguły niestandardowej kompilacji, która może być skojarzony z jedną lub więcej rozszerzeń nazw plików, umożliwia przekazywanie plików wejściowych do narzędzia, która tworzy jeden lub więcej plików wyjściowych.  
  
 W tej wersji reguły niestandardowej kompilacji są reprezentowane przez trzy typy plików, XML, .props i .targets, nie plikiem rules. Podczas migracji do bieżącej wersji pliku Rules, który został utworzony przy użyciu starszej wersji programu Visual C++ równoważne pliki XML, .props i .targets są tworzone i przechowywane w projekcie wraz z oryginalnego pliku rules.  
  
> [!IMPORTANT]
>  W bieżącej wersji [!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] nie obsługuje tworzenia nowych zasad. Z tego powodu Najprostszym sposobem użycia pliku reguł z projektu, który został utworzony przy użyciu starszej wersji programu Visual C++ jest wykonać migrację projektu do bieżącej wersji.  
  
## <a name="inheritance-macros"></a>Makra dziedziczenia  
 We wcześniejszych wersjach **$(Inherit)** makro określa kolejność wyświetlania właściwości dziedziczone w wierszu polecenia, który składa się przez system kompilacji projektu. **$(Noinherit) —** makro powoduje, że wszystkie wystąpienia $(Inherit) mają być ignorowane i powoduje, że wszystkie właściwości, które byłyby w innym przypadku dziedziczone, nie być dziedziczone. Na przykład domyślnie $(Inherit) — makro powoduje, że określono przy użyciu plików [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md) — opcja kompilatora mają być dołączane do wiersza polecenia.  
  
 W bieżącej wersji dziedziczenia jest obsługiwana przez określenie wartości właściwości jako łączenia wartości literałów oraz makra właściwości. **$(Inherit)** i **$(noinherit) —** makr nie są obsługiwane.  
  
 W poniższym przykładzie rozdzielaną średnikami listę jest przypisany do właściwości na stronie właściwości. Lista składa się łączenia  *\<wartość >* literał i wartość `MyProperty` właściwości, który jest dostępny przy użyciu notacji makra, **$(***MyProperty***)** .  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## <a name="vcxprojuser-files"></a>. vcxproj.user plików  
 Plik użytkownika (. vcxproj.user) przechowuje właściwości specyficzne dla użytkownika, na przykład, debugowanie i ustawienia wdrażania. Plik vcxproj.user odnosi się do wszystkich projektów dla danego użytkownika.  
  
## <a name="vcxprojfilters-file"></a>. vcxproj.filters pliku  
 Podczas **Eksploratora rozwiązań** służy do dodawania pliku do projektu, pliku filtrów (. vcxproj.filters) określa, gdzie w **Eksploratora rozwiązań** drzewa widoku, plik zostanie dodany, na podstawie ich rozszerzenia nazwy pliku.  
  
## <a name="vc-directories-settings"></a>Ustawienia katalogi VC ++  
 Visual C++ katalogów ustawienia są określone na [strona właściwości katalogów VC ++](../ide/vcpp-directories-property-page.md). We wcześniejszych wersjach programu Visual Studio katalogi ustawienia mają zastosowanie dla poszczególnych użytkowników i listę wykluczonych katalogów została określona w pliku sysincl.dat.  
  
 Nie można zmienić ustawienia katalogi VC ++, po uruchomieniu [devenv/resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) w wierszu polecenia. Również nie można zmienić ustawienia po otwarciu **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**, a następnie wybierz **zresetować wszystkie ustawienia** opcji.  
  
 Przeprowadź migrację ustawień katalogi VC ++ z plikiem .vssettings, który jest tworzony w przypadku wcześniejszych wersji programu Visual C++. Otwórz **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**, wybierz pozycję **Importuj wybrane ustawienia środowiska**, a następnie postępuj zgodnie z instrukcjami w kreatorze. Lub po uruchomieniu programu Visual Studio po raz pierwszy na **wybierz domyślne ustawienia środowiska** okno dialogowe, wybierz opcję **migracji ustawień kwalifikujących się od poprzedniej wersji i zastosować je oprócz ustawień domyślnych wybrany poniżej**.  
  
## <a name="see-also"></a>Zobacz też  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)