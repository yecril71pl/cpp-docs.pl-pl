---
title: "Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.walkthrough.createproject
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92b954f334517adc22ca17f8324ec1a78819d9f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Wskazówki: Korzystanie z MSBuild do tworzenia projektu Visual C++
W tym przewodniku przedstawiono sposób użycia [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] do tworzenia projektu Visual C++ w wierszu polecenia. Dowiesz się tworzenie pliki źródłowe C++ i pliku XML na podstawie projektu dla aplikacji konsoli języka Visual C++. Po utworzeniu projektu, dowiesz się, jak dostosować procesu kompilacji.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie C++ pliki źródłowe dla projektu.  
  
-   Tworzenie pliku XML [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] pliku projektu.  
  
-   Przy użyciu [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] Aby skompilować projekt.  
  
-   Przy użyciu [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] Aby dostosować projekt.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Potrzebne w tym przewodniku:  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   Zrozumienie ogólnego [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] systemu.  
  
## <a name="creating-the-c-source-files"></a>Tworzenie plików źródłowych C++  
 W tym przewodniku utworzy projekt, który zawiera plik źródłowy i plik nagłówka. Main.cpp plik źródłowy zawiera główną funkcją aplikacji konsoli. Main.h pliku nagłówka zawiera kod, aby uwzględnić plik nagłówka iostream. Te pliki C++ można tworzyć przy użyciu [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] lub edytora tekstu.  
  
#### <a name="to-create-the-c-source-files-for-your-project"></a>Aby utworzyć pliki źródłowe C++ dla projektu  
  
1.  Utwórz katalog projektu.  
  
2.  Utwórz plik o nazwie main.cpp i Dodaj następujący kod do tego pliku:  
  
    ```cpp  
    // main.cpp : the application source code.  
    #include <iostream>  
    #include "main.h"  
    int main()  
    {  
       std::cout << "Hello, from MSBuild!\n";  
       return 0;  
    }  
    ```  
  
3.  Utwórz plik o nazwie main.h i Dodaj następujący kod do tego pliku:  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## <a name="creating-the-xml-msbuild-project-file"></a>Tworzenie pliku projektu MSBuild XML  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] Plik projektu jest plik XML, który zawiera element główny projektu (\<projektu >). W poniższych przykładowy projekt \<projektu > element zawiera siedmiu elementów podrzędnych:  
  
-   Element trzy znaczniki grupy (\<ItemGroup >) określające konfiguracji projektu i platformy, nazwa pliku źródłowego i nazwa pliku nagłówka.  
  
-   Trzy importowanie znaczników (\<zaimportować >) które określają lokalizację ustawienia programu Microsoft Visual C++.  
  
-   Tag grupy właściwości (\<PropertyGroup >), który określa ustawienia projektu.  
  
#### <a name="to-create-the-msbuild-project-file"></a>Aby utworzyć plik projektu programu MSBuild  
  
1.  Użyj edytora tekstów, aby utworzyć plik projektu o nazwie `myproject.vcxproj`, a następnie dodaj poniższe głównego \<projektu > elementu. Wstaw elementy w poniższych krokach procedury między głównego \<projektu > tagów:  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  Dodaj następujące dwa \<ProjectConfiguration > elementy podrzędne w \<ItemGroup > elementu. Element podrzędny określa debug i release konfiguracje dla 32-bitowym systemie operacyjnym Windows:  
  
    ```xml  
    <ItemGroup>  
      <ProjectConfiguration Include="Debug|Win32">  
        <Configuration>Debug</Configuration>  
        <Platform>Win32</Platform>  
      </ProjectConfiguration>  
      <ProjectConfiguration Include="Release|Win32">  
        <Configuration>Release</Configuration>  
        <Platform>Win32</Platform>  
      </ProjectConfiguration>  
    </ItemGroup>  
  
    ```  
  
3.  Dodaj następujące \<Import / > element, który określa ścieżkę C++ domyślne ustawienia dla tego projektu:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  Dodaj następujący element grupy właściwości (\<PropertyGroup >), który określa dwie właściwości projektu:  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  Dodaj następujące \<Import / > element, który określa ścieżkę bieżące ustawienia C++ dla tego projektu:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  Dodaj następujące \<ClCompile > elementu podrzędnego w \<ItemGroup > elementu. Element podrzędny określa nazwę pliku źródłowego C/C++ do kompilacji:  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  Dodaj następujące \<ClInclude > elementu podrzędnego w \<ItemGroup > elementu. Element podrzędny określa nazwę pliku nagłówka dla pliku źródłowego C/C++:  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  Dodaj następujące \<Import > element, który określa ścieżkę pliku, który definiuje element docelowy dla tego projektu:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### <a name="complete-project-file"></a>Zakończenie pliku projektu  
 Poniższy kod przedstawia plik kompletnego projektu, który został utworzony w poprzedniej procedurze.  
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <ProjectConfiguration Include="Debug|Win32">  
      <Configuration>Debug</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|Win32">  
      <Configuration>Release</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
  </ItemGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  <PropertyGroup>  
    <ConfigurationType>Application</ConfigurationType>  
    <PlatformToolset>v120</PlatformToolset>  
  </PropertyGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
  <ItemGroup>  
    <ClCompile Include="main.cpp" />  
  </ItemGroup>  
  <ItemGroup>  
    <ClInclude Include="main.h" />  
  </ItemGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
</Project>  
```  
  
## <a name="using-msbuild-to-build-your-project"></a>Korzystanie z MSBuild do tworzenia projektu  
 Wpisz następujące polecenie w wierszu polecenia, aby skompilować aplikację konsoli:  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]Tworzy katalog dla plików wyjściowych, a następnie kompiluje i łączy z projektem, aby wygenerować Myproject.exe program. Po zakończeniu kompilacji, użyj następującego polecenia, aby uruchomić aplikację:  
  
```  
myproject  
```  
  
 Aplikacja powinien być wyświetlany "tekst Hello, z MSBuild!" w oknie konsoli.  
  
## <a name="customizing-your-project"></a>Dostosowywanie projektu  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]Umożliwia wykonanie kompilacji wstępnie zdefiniowanych celów, Zastosuj właściwości zdefiniowane przez użytkownika i użyj narzędzi niestandardowych zdarzeń i kroki procesu kompilacji. W tej części przedstawiono następujące zadania:  
  
-   Przy użyciu [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] z obiektami docelowymi kompilacji.  
  
-   Przy użyciu [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] z właściwościami kompilacji.  
  
-   Przy użyciu [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] z narzędzi i kompilatora 64-bitowych.  
  
-   Przy użyciu [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] z różnych procesami.  
  
-   Dodawanie [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] dostosowań.  
  
### <a name="using-msbuild-with-build-targets"></a>Przy użyciu programu MSBuild z obiektami docelowymi kompilacji  
 A *kompilacji docelowej* to nazwany zestaw wstępnie zdefiniowanych lub zdefiniowanych przez użytkownika poleceń, które mogą być wykonywane podczas kompilacji. Użyj opcji wiersza polecenia docelowego (**/t**) do określania docelowych kompilacji. W przypadku liczby `myproject` przykładowy projekt, wstępnie zdefiniowane **czystą** docelowy usuwa wszystkie pliki w folderze debugowania i tworzy nowy plik dziennika.  
  
 W wierszu polecenia wpisz następujące polecenie, aby wyczyścić `myproject`.  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### <a name="using-msbuild-with-build-properties"></a>Przy użyciu programu MSBuild z właściwości kompilacji  
 Opcja wiersza polecenia właściwości (**/p**) umożliwia zastąpienie właściwości w pliku projektu kompilacji. W `myproject` Przykładowa konfiguracja kompilacji projektu, wersji lub debug jest określona przez `Configuration` właściwości. I systemu operacyjnego, który jest przeznaczony do uruchamiania zbudowanych aplikacji jest określona przez `Platform` właściwości.  
  
 W wierszu polecenia wpisz następujące polecenie, aby utworzyć kompilacji debugowania `myproject` aplikacji, która jest przeznaczony do uruchamiania na 32-bitowego systemu Windows.  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 Przyjęto założenie, że `myproject` przykładowy projekt również definiuje konfigurację dla 64-bitowego systemu Windows i innego konfiguracji dla niestandardowego systemu operacyjnego o nazwie `myplatform`.  
  
 W wierszu polecenia wpisz następujące polecenie, aby utworzyć wersję kompilacji, która działa w 64-bitowym systemie Windows.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 W wierszu polecenia wpisz następujące polecenie, aby tworzenie kompilacji wydania dla `myplatform`.  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Przy użyciu programu MSBuild z narzędzi i kompilatora 64-bitowych  
 Po zainstalowaniu programu Visual C++ na 64-bitowym systemie Windows, domyślnie x64 64-bitowych natywne i Międzyplatformowe narzędzia są zainstalowane. Można skonfigurować [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] używać kompilator 64-bitowy i narzędzia do tworzenia aplikacji przez ustawienie `PreferredToolArchitecture` właściwości. Ta właściwość nie ma wpływu na właściwości konfiguracji lub platformy projektu. Domyślnie używany jest 32-bitowa wersja narzędzi. Aby określić 64-bitowej wersji narzędzi i kompilatora, Dodaj następujący element grupy właściwości do pliku projektu Myproject.vcxproj po `Microsoft.Cpp.default.props` \<Import / > elementu:  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 W wierszu polecenia wpisz następujące polecenie, aby skompilować aplikację za pomocą narzędzi 64-bitowych.  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="using-msbuild-with-a-different-toolset"></a>Przy użyciu programu MSBuild z innego zestawu narzędzi  
 Jeśli masz procesami i bibliotek dla innych wersji programu Visual C++, zainstalowane, [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] mogą tworzyć aplikacje dla dowolnego bieżącej wersji programu Visual C++ lub dla siebie zainstalowanej wersji. Na przykład, jeśli zainstalowano [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], aby określić zestaw narzędzi Visual C++ 11.0 dla systemu Windows XP, Dodaj następujący element grupy właściwości do pliku projektu Myproject.vcxproj po Microsoft.Cpp.props `<Import />` elementu:  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 Aby ponownie skompiluj projekt z zestawu narzędzi programu Visual C++ 11.0 systemu Windows XP, wpisz jedno z następujących poleceń:  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### <a name="adding-msbuild-customizations"></a>Dodawanie dostosowań MSBuild  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]udostępnia różne sposoby dostosowania procesu kompilacji. W następujących tematach opisano sposób dodawania niestandardowe kroki procesu kompilacji, narzędzia i zdarzenia do użytkownika [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] projektu:  
  
-   [Instrukcje: dodawanie niestandardowego kroku kompilacji do projektów MSBuild](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [Instrukcje: dodawanie niestandardowych narzędzi kompilacji do projektów MSBuild](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [Instrukcje: korzystanie ze zdarzeń kompilacji w projektach MSBuild](../build/how-to-use-build-events-in-msbuild-projects.md)