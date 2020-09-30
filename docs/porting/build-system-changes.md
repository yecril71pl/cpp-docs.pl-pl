---
title: VCBuild a MSBuild
description: System kompilacji VIsual Studio C++ został zmieniony z VCBuild na MSBuild w programie Visual Studio 2010.
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: b1b963aca3de75cf9852c55f59a99422568ab4b4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91505918"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild a MSBuild: Kompiluj zmiany systemu w programie Visual Studio 2010

System MSBuild dla projektów języka C++ został wprowadzony w programie Visual Studio 2010. W programie Visual Studio 2008 i wcześniejszych wersjach został użyty system VCBuild. Niektóre typy plików i pojęcia, które są zależne od VCBuild, nie istnieją lub są reprezentowane inaczej w programie MSBuild. W tym dokumencie omówiono różnice w bieżącym systemie kompilacji. Aby przekonwertować projekt programu Visual Studio 2008 na MSBuild, należy użyć programu Visual Studio 2010. Po przekonwertowaniu projektu należy użyć najnowszej wersji programu Visual Studio, aby przeprowadzić uaktualnienie do bieżącego zestawu narzędzi IDE i kompilatora. Aby uzyskać więcej informacji, w tym informacje na temat sposobu uzyskania programu Visual Studio 2010, zobacz [instrukcje dla programu Visual studio 2008](use-native-multi-targeting.md#instructions-for-visual-studio-2008).

W poniższych sekcjach podsumowano zmiany z programu VCBuild do programu MSBuild. Jeśli projekt VCBuild ma niestandardowe reguły kompilacji lub makra, które nie są rozpoznawane przez program MSBuild, zobacz [Visual Studio projects-C++](../build/creating-and-managing-visual-cpp-projects.md) , aby dowiedzieć się, jak przetłumaczyć te instrukcje do systemu MSBuild. Początkowa konwersja z VCBuild na MSBuild jest po kroku pośrednim. Nie jest konieczne pobieranie pliku projektu w całości lub uzyskanie programu do skompilowania bez błędów. Używasz tylko programu Visual Studio 2010 do przekonwertowania projektu na format MSBuild, aby projekt działał w najnowszej wersji programu Visual Studio.

## <a name="vcproj-is-now-vcxproj"></a>. vcproj to teraz. vcxproj

Pliki projektu nie używają już rozszerzenia nazwy pliku. vcproj. Program Visual Studio 2010 automatycznie konwertuje pliki projektu, które zostały utworzone przez wcześniejszą wersję Visual C++ do formatu MSBuild, który używa rozszerzenia. vcxproj dla plików projektu.

## <a name="vsprops-is-now-props"></a>. VSPROPS jest teraz. props

W programie Visual Studio 2008 i starszych, *Arkusz właściwości projektu* jest plikiem opartym na formacie XML, który ma rozszerzenie nazwy pliku. VSPROPS. Arkusz właściwości projektu pozwala określić przełączniki dla narzędzi do kompilacji, takie jak kompilator lub konsolidator, i utworzyć makra zdefiniowane przez użytkownika. W programie MSBuild rozszerzenie nazwy pliku arkusza właściwości projektu to. props.

## <a name="custom-build-rules-and-rules-files"></a>Niestandardowe reguły kompilacji i pliki reguł

W programie Visual Studio 2008 i starszych, *plik reguł* jest plikiem opartym na formacie XML, który ma rozszerzenie nazwy pliku. rules. Plik reguły umożliwia zdefiniowanie niestandardowych reguł kompilacji i włączenie ich do procesu kompilacji projektu Visual Studio C++. Niestandardowa reguła kompilacji, która może być skojarzona z co najmniej jednym rozszerzeniem nazwy pliku, umożliwia przekazywanie plików wejściowych do narzędzia, które tworzy jeden lub więcej plików wyjściowych.

W systemie MSBuild niestandardowe reguły kompilacji są reprezentowane przez trzy typy plików,. XML,. props i. targets zamiast pliku reguł. Gdy plik. rules, który został utworzony przy użyciu wcześniejszej wersji Visual C++, zostanie zmigrowany do programu Visual Studio 2010, równoważne. XML,. props i. targets są tworzone i przechowywane w projekcie wraz z oryginalnym plikiem. rules.

> [!IMPORTANT]
> W programie Visual Studio 2010 środowisko IDE nie obsługuje tworzenia nowych reguł. Z tego powodu Najprostszym sposobem użycia pliku reguły z projektu, który został utworzony przy użyciu wcześniejszej wersji Visual C++ jest Migrowanie projektu do programu Visual Studio 2010.

## <a name="inheritance-macros"></a>Makra dziedziczenia

W programie Visual Studio 2008 i starszych, makro **$ (Inherit)** określa kolejność, w której dziedziczone właściwości pojawiają się w wierszu polecenia, który jest tworzony przez system kompilacji projektu. Makro **$ (NoInherit)** powoduje ignorowanie wszystkich wystąpień elementu $ (Inherit) i powoduje, że wszystkie właściwości, które w przeciwnym razie byłyby dziedziczone, nie są dziedziczone. Na przykład domyślnie makro $ (Inherit) powoduje, że pliki określone przy użyciu opcji kompilatora [/i (Dodatkowe katalogi dołączane)](../build/reference/i-additional-include-directories.md) mają być dołączane do wiersza polecenia.

W programie Visual Studio 2010 dziedziczenie jest obsługiwane przez określenie wartości właściwości jako łączenia jednej lub więcej wartości literału i makr właściwości. Makra **$ (Inherit)** i **$ (NoInherit)** nie są obsługiwane.

W poniższym przykładzie lista rozdzielana średnikami jest przypisana do właściwości na stronie właściwości. Lista składa się z łączenia *\<value>* literału i wartości `MyProperty` właściwości, do której uzyskuje się dostęp przy użyciu notacji makro **$ (**<em>Właściwości</em>**)**.

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>. vcxproj. User — pliki

Plik użytkownika (. vcxproj. user) przechowuje właściwości specyficzne dla użytkownika, na przykład ustawienia debugowania i wdrażania. Plik *vcxproj. User* ma zastosowanie do wszystkich projektów dla określonego użytkownika.

## <a name="vcxprojfilters-file"></a>plik. vcxproj. filters

Gdy **Eksplorator rozwiązań** jest używany do dodawania pliku do projektu, plik filtrów (*. vcxproj. filters*) definiuje, gdzie w widoku drzewa **Eksplorator rozwiązań** plik zostanie dodany na podstawie jego rozszerzenia nazwy pliku.

## <a name="vc-directories-settings"></a>Ustawienia katalogów VC + +

Ustawienia katalogów Visual C++ są określone na [stronie właściwości Katalogi VC + +](../build/reference/vcpp-directories-property-page.md). W programie Visual Studio 2008 i wcześniejszych ustawienia katalogów dotyczą poszczególnych użytkowników, a lista wykluczonych katalogów jest określona w pliku *sysincl. dat* .

Nie można zmienić ustawień katalogów VC + +, jeśli uruchomisz [devenv/ResetSettings](/visualstudio/ide/reference/resetsettings-devenv-exe) w wierszu polecenia. Nie można również zmienić ustawień, jeśli otworzysz menu **Narzędzia** , kliknij przycisk **Importuj i Eksportuj ustawienia**, a następnie wybierz opcję **Zresetuj wszystkie ustawienia** .

Aby przeprowadzić migrację ustawień katalogów VC + + z pliku *VSSETTINGS* , który został utworzony przez wcześniejszą wersję programu Visual Studio:

1. Otwórz menu **Narzędzia** , kliknij pozycję **Importuj i Eksportuj ustawienia** .
2. Wybierz opcję **Importuj wybrane ustawienia środowiska**
3. Postępuj zgodnie z instrukcjami wyświetlanymi w kreatorze.

## <a name="see-also"></a>Zobacz też

[MSBuild w wierszu polecenia — C++](../build/msbuild-visual-cpp.md)
