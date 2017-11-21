---
title: "Struktura plików .vcxproj i .props | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 04/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
caps.latest.revision: "1"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bc57a69b71bd7fbdbf97d5c34e7e6ec0694bb5df
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vcxproj-and-props-file-structure"></a>Struktura pliku .vcxproj i .props
MSBuild jest domyślny system projektu programu Visual Studio; Po wybraniu **pliku | Nowy projekt** w programie Visual C++ tworzenia projektu programu MSBuild, których ustawienia są przechowywane w pliku projektu XML, który ma rozszerzenie `.vcxproj`. Plik projektu może również zaimportować pliki .props i pliki .targets przechowywania ustawień. W większości przypadków nie trzeba ręcznie zmodyfikować plik projektu, a w rzeczywistości nie należy edytować go ręcznie, chyba że dysponować dobrą znajomością programu MSBuild. W miarę możliwości należy używać na stronach właściwości programu Visual Studio Aby zmodyfikować ustawienia projektu (zobacz [Praca z właściwościami projektu](working-with-project-properties.md). Jednak w niektórych przypadkach należy ręcznie zmodyfikować plik lub właściwości arkusza projektu. W tych scenariuszach ten artykuł zawiera podstawowe informacje na temat struktury pliku. 

**Ważne:** Jeśli użytkownik chce ręcznie edytować plik .vcxproj, należy pamiętać o tych zdarzeniach:
1. Struktura pliku musi następować po wyznaczonych formularza, który jest opisany w tym artykule.
2. System projektu Visual C++ aktualnie nie obsługuje symboli wieloznacznych w elementach projektu. Na przykład to nie jest obsługiwana:
```xml
<ClCompile Include="*.cpp"/>
```
3. System projektu Visual C++ aktualnie nie obsługuje makra w ścieżkach elementów projektu. Na przykład to nie jest obsługiwana:
```xml
<ClCompile Include="$(IntDir)\generated.cpp"/>
```
4. Aby przypisać właściwości projektu poprawnie dodane, usunięte lub zmodyfikowane podczas edycji w **właściwości projektu** okna dialogowego, plik musi zawierać oddzielne grupy dla każdej konfiguracji projektu i warunki musi należeć do tego formularza:

```xml
Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”
```
 
5. Należy określić każdej właściwości w grupie z prawidłowa etykieta, jak określono w pliku reguł właściwości. Aby uzyskać więcej informacji, zobacz [plików reguł xml strony właściwości] (https://review.docs.microsoft.com/en-us/cpp/ide/property-page-xml-files). 


## <a name="vcxproj-file-elements"></a>elementy pliku .vcxproj
Zawartość pliku .vcxproj można sprawdzić za pomocą dowolnego tekstu lub edytora XML. Można wyświetlić w programie Visual Studio przez kliknięcie prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wybierając **Zwolnij projekt** , a następnie wybierając **Edytuj Foo.vcxproj**. 

Przede wszystkim należy zauważyć, to czy najwyższego poziomu elementy są widoczne w określonej kolejności. Na przykład:
-  Większość właściwości grup i grup definicji elementu występować po zaimportowaniu dla Microsoft.Cpp.Default.props.
-  wszystkie elementy docelowe są importowane na końcu pliku.
-  istnieje wiele grup właściwości, z których każda z unikatową etykietę, oraz ich w określonej kolejności.

Kolejność elementów w pliku projektu jest bardzo ważne, ponieważ program MSBuild jest oparta na modelu sekwencyjnych oceny.  Jeśli Twojego pliku projektu, w tym wszystkich importowanych .props i pliki .targets zawiera wiele definicji właściwości, ostatni definicji zastąpienia poprzedniego te. W poniższym przykładzie wartość "ciągu xyz" zostanie ustawiona podczas kompilacji, ponieważ napotka ostatni go podczas jego obliczania aparat MSBUild. 

```xml 
 <MyProperty>abc</MyProperty>
 <MyProperty>xyz</MyProperty>
``` 
 
Poniższy fragment kodu przedstawia plik .vcxproj minimalny. Każdy plik .vcxproj, generowane przez program Visual Studio będzie zawierać tych elementów MSBuild najwyższego poziomu, a pojawią się w następującej kolejności (chociaż mogą zawierać wiele kopii każdego elementu najwyższego poziomu). Należy pamiętać, że `Label` atrybuty są dowolne tagi, które są używane tylko przez program Visual Studio jako signposts do edycji, nie mają innych funkcji.

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003'>
   <ItemGroup Label="ProjectConfigurations" />
   <PropertyGroup Label="Globals" />
   <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
   <PropertyGroup Label="Configuration" />
   <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
   <ImportGroup Label="ExtensionSettings" />
   <ImportGroup Label="PropertySheets" />
   <PropertyGroup Label="UserMacros" />
   <PropertyGroup />
   <ItemDefinitionGroup />
   <ItemGroup />
   <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
   <ImportGroup Label="ExtensionTargets" />
 </Project>
```
 
 W poniższej sekcji opisano przeznaczenie każdej z tych elementów i dlaczego są one uporządkowane w ten sposób:
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```
`Project`jest to węzeł główny. Określa wersję MSBuild do użycia, a także docelowy domyślna ma być wykonywana w przypadku ten plik jest przekazywany do MSBuild.exe.

```xml  
<ItemGroup Label="ProjectConfigurations" />
```
`ProjectConfigurations`Zawiera opis konfiguracji projektu. Przykłady debugowania | Win32, wersja | Win32, debugowania | ARM i tak dalej. Wiele ustawień projektu są specyficzne dla danej konfiguracji. Na przykład prawdopodobnie można ustawić właściwości optymalizacji kompilacji wydania, ale nie kompilację debugowania.  

Poniższy fragment kodu przedstawia konfigurację projektu. W tym przykładzie "Debug | x 64 jest nazwa konfiguracji. Nazwa konfiguracji projektu musi być w formacie $(Configuration)|$(Platform). Węzeł konfiguracji projektu może mieć dwie właściwości: Configuration i Platform. Te właściwości zostaną automatycznie ustawione przy użyciu wartości określonej w tym miejscu, gdy konfiguracja jest aktywny.

```xml
<ProjectConfiguration Include="Debug|x64">
    <Configuration>Debug</Configuration> 
    <Platform>x64</Platform>
</ProjectConfiguration>
```
`ProjectConfigurations` Grupy elementów nie jest używany w czasie kompilacji. Środowiska IDE programu Visual Studio wymagają, aby można było załadować projekt. Ta grupa można przenieść pliku .props i importowane do pliku .vcxproj. Jednak w takim przypadku, jeśli musisz dodać lub usunąć konfiguracji, należy ręcznie zmienić plik .props; Nie można użyć IDE.

IDE oczekuje można znaleźć konfiguracji projektu dla dowolnej kombinacji wartości Configuration i Platform używane we wszystkich elementach ProjectConfiguration. Często oznacza to, że projekt może mieć konfiguracje projektu znaczenia do spełnienia tego wymagania. Na przykład jeśli projekt ma następujące konfiguracje:

- Debugowanie | Win32
- Detaliczne | Win32
- Specjalne optymalizacji 32-bitowych | Win32

następnie musi mieć jednak również te konfiguracje, mimo że "Specjalne optymalizacji 32-bitowe" nie ma znaczenia dla x64: 

- Debugowanie | x64
- Detaliczne | x64
- Specjalne optymalizacji 32-bitowych | x64

Można wyłączyć kompilacji i wdrażania polecenia dla żadnej konfiguracji w Menedżerze konfiguracji rozwiązania.

```xml  
 <PropertyGroup Label="Globals" />
```
 `Globals`zawiera ustawienia poziomu projektu, takie jak ProjectGuid, RootNamespace i atrybutów ApplicationType / ApplicationTypeRevision. Ostatnie dwa często zdefiniować docelowy system operacyjny. Projekt tylko można kierować jednego systemu operacyjnego na fakt, że odwołania i elementy projektu nie może mieć warunki obecnie. Te właściwości zwykle nie są nadpisywane w innym miejscu w pliku projektu. Ta grupa nie jest zależne od konfiguracji i w związku z tym zazwyczaj tylko jedna grupa Globals istnieje w pliku projektu.

```xml
 <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Microsoft.Cpp.default.props** arkusz właściwości jest dostarczany z programem Visual Studio i nie może być modyfikowany. Zawiera ustawienia domyślne dla projektu. Ustawienia domyślne mogą się różnić w zależności od atrybutów ApplicationType.

```xml
<PropertyGroup Label="Configuration" />
```
 `Configuration` Grupy właściwości zawiera warunek dołączone konfiguracji (takich jak `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) i składa się z wielu kopii, po jednym dla każdego konfiguracji. Tej właściwości grupy hostów właściwości, które są ustawiane dla określonej konfiguracji. Właściwości konfiguracji obejmują jest zestaw narzędzi platformy i kontrolować również włączenia systemu arkuszy właściwości w **Microsoft.Cpp.props**. Na przykład, jeśli zdefiniowano właściwość `<CharacterSet>Unicode</CharacterSet>`, następnie systemowy arkusz właściwości **firmy microsoft. CPP.unicodesupport.props** zostaną uwzględnione. Jeśli sprawdzenie **Microsoft.Cpp.props**, zostanie wyświetlony wiersz: `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`. 

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```
**Microsoft.Cpp.props** arkusza właściwości (bezpośrednio lub za pośrednictwem importów) definiuje wartości domyślne dla wielu właściwości określonym dla narzędzia, takie jak kompilatora optymalizacji i poziom ostrzeżeń właściwości TypeLibraryName narzędzie MIDL właściwości i tak dalej. Importuje różnych arkuszy właściwości systemu oparte na właściwości konfiguracji, które są zdefiniowane w grupie właściwości bezpośrednio powyżej. 

```xml
<ImportGroup Label="ExtensionSettings" />
```
`ExtensionSettings` Grupa zawiera Importy dla arkuszy właściwości, które są częścią dostosowania kompilacji. Dostosowanie kompilacji jest definiowana za pomocą maksymalnie trzy pliki: plik .targets, pliku .props i pliku XML. Ta grupa importu zawiera polecenie importuje plik .props.

```xml
<ImportGroup Label="PropertySheets" />
```
 `PropertySheets` Grupa zawiera Importy dla arkusz właściwości użytkownika. Są to arkuszy właściwości, które dodajesz za pośrednictwem Menedżera właściwości widoku w programie Visual Studio. Kolejność, w którym są wyświetlane te importów ważne jest i jest widoczny w Menedżerze właściwości. Plik projektu zawiera zazwyczaj wiele wystąpień tego typu grupy importu, jeden dla każdej konfiguracji projektu.  
   
```xml   
<PropertyGroup Label="UserMacros" />
```
`UserMacros`są jako zmienne, które są używane w celu dostosowania procesu kompilacji. Na przykład można zdefiniować makro użytkownika do definiowania ścieżce danych wyjściowych niestandardowego jako $(CustomOutputPath) i użyj go do zdefiniowania pozostałe zmienne. Ta grupa właściwość przechowuje takich właściwości. Należy pamiętać, że w programie Visual Studio, ta grupa nie zostanie wypełnione w pliku projektu ponieważ Visual C++ nie obsługuje konfiguracji makra użytkownika. Makra użytkownika są obsługiwane w arkuszach właściwości. 

```xml
<PropertyGroup />
``` 
 Ta grupa właściwości mogą mieć warunku konfiguracji dołączony w przypadku wszystkich konfiguracji projektu. Jeżeli dowolne brakuje okna dialogowego właściwości projektu nie będzie działać prawidłowo. Istnieje wiele wystąpień grupy właściwości, po jednym dla każdego konfiguracji. W odróżnieniu od powyższej grup właściwości ta nie ma etykiety. Ta grupa zawiera ustawienia konfiguracji na poziomie projektu. Te ustawienia mają zastosowanie do wszystkich plików, które są częścią grupy określony element. Definicja elementu dostosowania kompilacji tutaj zainicjowano metadanych. Ta PropertyGroup musi występować po `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` i nie może być nie innych PropertyGroup bez etykiety przed (w przeciwnym razie edycji właściwości projektu nie będzie działać poprawnie).  

```xml
 <ItemDefinitionGroup />
```
Zawiera definicje elementów. Muszą one zgodne z regułami warunki jako PropertyGroup bez etykiety.

```xml
<ItemGroup />
```  
Zawiera elementy (pliki źródłowe, itp.) w projekcie. Warunki nie są obsługiwane w przypadku elementów projektu (tzn. element typy, które są traktowane jako elementy projektu przez definicje zasady).

Metadane powinny mieć warunki konfiguracji dla każdej konfiguracji, nawet jeśli theyare te same. Na przykład:

  ```xml
  <ItemGroup>
     <ClCompile Include="stdafx.cpp">
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
       <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
     </ClCompile>
  </ItemGroup>
  ```
System projektu Visual C++ aktualnie nie obsługuje symboli wieloznacznych w elementach projektu. 
```xml  
  <ItemGroup>
     <ClCompile Include="*.cpp"> <!--Error-->
  </ItemGroup>
```
System projektu Visual C++ aktualnie nie obsługuje makra w elementach projektu. 
```xml  
  <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
  </ItemGroup>
```
Odwołania są określone w ItemGroup i mają następujące ograniczenia:
- Odwołania nie obsługują warunki. 
- Odwołania do metadanych nie obsługują warunki.

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```
Definiuje (bezpośrednio lub za pośrednictwem importów) obiekty docelowe Visual C++, takie jak kompilacji, wyczyść itp.

```xml
<ImportGroup Label="ExtensionTargets" />
```
Ta grupa zawiera Importy dla docelowej pliki dostosowania kompilacji.
 
 ## <a name="impact-of-incorrect-ordering"></a>Niepoprawna kolejność wpływ
 Środowiska IDE programu Visual Studio jest zależna od projektu pliku o kolejność opisane powyżej. Na przykład po zdefiniowaniu wartość właściwości na stronach właściwości IDE zazwyczaj umieści definicji właściwości w grupie właściwości z etykietą puste. Dzięki temu, że wartości domyślne w arkuszach właściwości systemu są zastępowane przez wartości zdefiniowanych przez użytkownika. Podobnie na końcu są importowane pliki docelowe, ponieważ zużywają właściwości zdefiniowanych powyżej i ponieważ zazwyczaj nie definiują właściwości samodzielnie. Podobnie, arkusz właściwości użytkownika są importowane po arkuszach właściwości systemu (włączone za pośrednictwem **Microsoft.Cpp.props**). Dzięki temu, że użytkownik można zastąpić wartości domyślne, sprowadzonych przez arkusze właściwości systemu.
  
 Jeśli plik .vcxproj nie jest zgodna z tym układzie, wyniki kompilacji nie może być oczekiwań. Na przykład po zaimportowaniu przez pomyłkę systemowym arkuszem właściwości po arkuszach właściwości zdefiniowane przez użytkownika, ustawienia użytkownika zostaną zastąpione przez arkusze właściwości systemu.
  
 Nawet środowiska czasu projektowania IDE zależy w pewnym stopniu kolejności poprawne elementów. Na przykład, jeśli nie ma pliku .vcxproj `PropertySheets` grupie importu, IDE może nie być możliwe ustalenie, gdzie umieścić nowy arkusz właściwości utworzony w **Menedżer właściwości**. Może to spowodować arkusz użytkownika zastępowanej przez arkusz systemu. Mimo że Algorytm heurystyczny używany przez IDE może tolerować niewielkie niespójności w układzie plik .vcxproj, zaleca się nie różni się od struktury przedstawionej w tym artykule.

## <a name="how-the-ide-uses-element-labels"></a>Używaniu środowiska IDE etykiety elementu
  
W środowisku IDE programu po ustawieniu właściwości UseOfAtl na stronie właściwości ogólnych jest ona zapisywana w grupie właściwości konfiguracji w pliku projektu, gdy wartość właściwości TargetName w tej samej stronie właściwości są zapisywane w grupie właściwości bez etykiety. Visual Studio wygląda na stronie właściwości pliku xml informacji o tym, gdzie można zapisać każdej właściwości. Na stronie Ogólne właściwości (przy założeniu, masz angielską wersję programu Visual Studio Enterprise Edition), czy plik jest `%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Plik reguł XML strony właściwości definiuje statyczne informacje na temat reguły i jego właściwości. Jeden zestaw takich informacji jest preferowanym pozycja właściwości reguły w pliku docelowym (plik, w którym zostanie zapisany jej wartość). Pozycja preferowany jest określona przez atrybut etykiety w elementach pliku projektu. 


 ## <a name="property-sheet-layout"></a>Układ arkusza właściwości
  
 Następujący fragment kodu XML jest minimalnym układ pliku (.props) arkusza właściwości. Przypomina plik .vcxproj, a funkcjonalność elementy .props można wywnioskować na podstawie wcześniej dyskusji. 

```xml
 <Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <ImportGroup Label="PropertySheets" />
   <PropertyGroup Label="UserMacros" />
   <PropertyGroup />
   <ItemDefinitionGroup />
   <ItemGroup />
 </Project>
```
Aby wprowadzić własny arkusza właściwości, skopiować jeden z plików .props w folderze VCTargets, a następnie zmodyfikować go do własnych celów. Dla programu Visual Studio 2017 Enterprise edition, jest domyślną ścieżkę VCTargets `%ProgramFiles%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets`. 

## <a name="see-also"></a>Zobacz też
[Praca z właściwościami projektu](working-with-project-properties.md)
[pliki XML strony właściwości](property-page-xml-files.md)