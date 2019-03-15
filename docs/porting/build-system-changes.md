---
title: Build System Changes in Visual Studio 2010
ms.date: 11/04/2016
f1_keywords:
- vc.msbuild.changes
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: 621e62379657da66d6eaec7a3ceff780fd610066
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823969"
---
# <a name="build-system-changes"></a>Zmiany systemu kompilacji

MSBuild system jest używany do tworzenia projektów Visual C++. Jednak w programie Visual Studio 2008 i jego starszych wersji systemu program VCBuild był używany. Niektóre typy plików i pojęcia, które są zależne od program VCBuild nie istnieją lub są reprezentowane w różny sposób w obecnym systemie. W tym dokumencie omówiono różnice w obecnym systemie kompilacji.

## <a name="vcproj-is-now-vcxproj"></a>.VCPROJ jest teraz .vcxproj

Pliki projektu nie są już używane .vcproj rozszerzenie nazwy pliku. Program Visual Studio automatycznie konwertuje pliki projektu, które zostały utworzone przez starszej wersji programu Visual C++ do formatu, który jest używany przez bieżącego systemu. Aby uzyskać więcej informacji na temat ręcznego uaktualnienia projektu, zobacz [/Upgrade (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).

W bieżącej wersji rozszerzenia nazwy pliku dla pliku projektu jest .vcxproj.

## <a name="vsprops-is-now-props"></a>.vsprops — jest teraz .props

We wcześniejszych wersjach *arkusz właściwości projektu* jest plik oparty na formacie XML, który ma rozszerzenie nazwy pliku .vsprops. Arkusz właściwości projektu umożliwia określenia przełączniki kompilacji narzędzia, takie jak kompilator lub konsolidator i utworzyć makra zdefiniowane przez użytkownika.

W bieżącej wersji rozszerzenie nazwy pliku dla arkusza właściwości projektu jest .props.

## <a name="custom-build-rules-and-rules-files"></a>Niestandardowej kompilacji, reguł i pliki Rules

We wcześniejszych wersjach *pliku reguł* jest plik oparty na formacie XML, który ma rozszerzenie nazwy pliku rules. Plik reguł pozwala zdefiniować niestandardowe reguły kompilacji i dołączyć je do procesu tworzenia projektu Visual C++. Reguły niestandardowej kompilacji, która może być skojarzony z jedną lub więcej rozszerzeń nazw plików, umożliwia przekazywanie plików wejściowych do narzędzia, która tworzy jeden lub więcej plików wyjściowych.

W tej wersji niestandardowych regułach kompilacji są reprezentowane przez trzy typy plików, XML, .props i .targets, a nie plikiem rules. Gdy plik Rules, który został utworzony przy użyciu starszej wersji programu Visual C++ jest migrowana do bieżącej wersji, równoważne pliki XML, .props i .targets są tworzone i przechowywane w projekcie, wraz z oryginalnego pliku rules.

> [!IMPORTANT]
>  W bieżącej wersji środowiska IDE nie obsługuje tworzenia nowych zasad. Z tego powodu Najprostszym sposobem przy użyciu pliku reguł z projektu, który został utworzony przy użyciu starszej wersji programu Visual C++ jest przeprowadzić migrację projektu do bieżącej wersji.

## <a name="inheritance-macros"></a>Makra dziedziczenia

We wcześniejszych wersjach **$(Inherit)** makro określa kolejność, w jakiej są wyświetlane właściwości dziedziczonych w wierszu polecenia, który składa się przez system kompilacji projektu. **$(NoInherit)** makro powoduje, że wszystkie wystąpienia $(Inherit) mają być ignorowane i powoduje, że wszystkie właściwości, które mogłyby w przeciwnym razie można dziedziczyć, nie być dziedziczone. Na przykład domyślnie $(Inherit) — makro powoduje, że określono za pomocą plików [/I (dodatkowe katalogi dołączenia)](../build/reference/i-additional-include-directories.md) opcję kompilatora, które mają być dołączane do wiersza polecenia.

W bieżącej wersji obsługiwane jest dziedziczenie, określając wartość właściwości jako łączenia jednej lub więcej wartości literału, jak i makra właściwości. **$(Inherit)** i **$(NoInherit)** makra nie są obsługiwane.

W poniższym przykładzie rozdzielaną średnikami listę jest przypisany do właściwości na stronie właściwości. Lista składa się łączenia  *\<wartość >* literału i wartością `MyProperty` właściwość, która jest dostępne przy użyciu notacji makra, **$(**  <em>MyProperty</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj.user Files

Plik użytkownika (. vcxproj.user) przechowuje właściwości specyficzne dla użytkownika, na przykład, debugowanie i wdrażanie ustawień. Plik vcxproj.user ma zastosowanie do wszystkich projektów dla danego użytkownika.

## <a name="vcxprojfilters-file"></a>. vcxproj.filters pliku

Podczas **Eksploratora rozwiązań** służy do dodawania pliku do projektu, plik filtrów (. vcxproj.filters) określa, gdzie w **Eksploratora rozwiązań** drzewa widoku, plik zostanie dodany, oparte na rozszerzenie nazwy pliku.

## <a name="vc-directories-settings"></a>Ustawienia katalogi VC ++

Ustawienia katalogi Visual C++ są określone na [VC ++ Directories Property Page](../ide/vcpp-directories-property-page.md). We wcześniejszych wersjach programu Visual Studio, katalogi ustawienia dotyczą poszczególnych użytkowników i listę wykluczonych katalogów została określona w pliku sysincl.dat.

Nie można zmienić ustawienia katalogi VC ++, po uruchomieniu [devenv/resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) w wierszu polecenia. Również nie można zmienić ustawienia po otwarciu **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**, a następnie wybierz pozycję **Resetuj wszystkie ustawienia** opcji.

Z pliku .vssettings, który jest tworzony przez starszej wersji programu Visual C++, należy przeprowadzić migrację ustawień katalogi VC ++. Otwórz **narzędzia** menu, kliknij przycisk **Import i eksport ustawień**, wybierz opcję **Importuj ustawienia wybranego środowiska**, a następnie postępuj zgodnie z instrukcjami wyświetlanymi w kreatorze. Lub po uruchomieniu programu Visual Studio po raz pierwszy w **wybierz domyślnych ustawień środowiska** okno dialogowe, wybierz opcję **migrację swoich kwalifikujących się ustawień z poprzedniej wersji, a następnie zastosuj je oprócz ustawienia domyślne wybrane poniżej**.

## <a name="see-also"></a>Zobacz także

[Program MSBuild w wierszu polecenia — C++](../build/msbuild-visual-cpp.md)
