---
title: Struktura plików vcxproj i props
ms.date: 05/16/2019
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 86c393796b1ce3efdb92d8aefd1f653390619ea4
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837515"
---
# <a name="vcxproj-and-props-file-structure"></a>Struktura plików vcxproj i props

[MSBuild](../msbuild-visual-cpp.md) jest domyślny system projektu w programie Visual Studio; w przypadku wybrania **pliku** > **nowy projekt** Visual C++ służy do utworzenia projektu programu MSBuild, których ustawienia są przechowywane. w pliku XML projektu, który ma rozszerzenie `.vcxproj`. Plik projektu może również zaimportować pliki .props i plików .targets, w których są przechowywane ustawienia. W większości przypadków nie jest konieczna ręczna Edycja pliku projektu, a w rzeczywistości nie należy edytować go ręcznie, chyba że dysponować dobrą znajomością programu MSBuild. W miarę możliwości należy używać stron właściwości w programie Visual Studio na modyfikowanie ustawień projektu (zobacz [kompilatora i tworzenia właściwości ustaw C++ w programie Visual Studio](../working-with-project-properties.md). Jednak w niektórych przypadkach może być konieczne ręcznie zmodyfikować arkusz pliku lub właściwości projektu. W tych scenariuszach ten artykuł zawiera podstawowe informacje na temat struktury pliku.

**Ważne:**

Jeśli użytkownik chce ręcznie edytować plik .vcxproj, należy pamiętać o tych zdarzeniach:

1. Struktura pliku, należy wykonać realizowania formularza, który jest opisany w tym artykule.

1. Visual Studio C++ system projektu aktualnie nie obsługuje symboli wieloznacznych w elementach projektu. Na przykład to nie jest obsługiwana:

   ```xml
   <ClCompile Include="*.cpp"/>
   ```

1. Visual Studio C++ system projektu aktualnie nie obsługuje makr w ścieżkach elementów projektu. Na przykład to nie jest obsługiwana:

   ```xml
   <ClCompile Include="$(IntDir)\generated.cpp"/>
   ```

   "Nie jest obsługiwane" oznacza, że makra nie musi działać dla wszystkich operacji w środowisku IDE. Makra, które nie zmieniają się ich wartości w różnych konfiguracjach powinna działać, ale nie mogą zostać zachowane, jeśli element zostanie przeniesiony do innego filtru lub projektu. Makra, które zmieniają się ich wartości dla różnych konfiguracji spowoduje problemy, ponieważ IDE nie oczekuje się różnić w przypadku konfiguracji z innego projektu ścieżki elementu projektu.

1. Aby uzyskać właściwości projektu poprawnie dodane, usunięte lub zmodyfikowane podczas edycji w **właściwości projektu** okno dialogowe, plik musi zawierać osobnych grup dla każdej konfiguracji projektu i warunki muszą być w tym formularzu:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

1. Każda właściwość należy określić w grupie z poprawną etykiety, jak to określono w pliku reguł właściwości. Aby uzyskać więcej informacji, zobacz [pliki reguł xml strony właściwości](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>elementy w pliku .vcxproj

Za pomocą dowolnego tekstu lub edytorze XML, można sprawdzić zawartość pliku .vcxproj. Można wyświetlić w programie Visual Studio przez kliknięcie prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wybierając **Zwolnij projekt** , a następnie wybierając **Edytuj Foo.vcxproj**.

Przede wszystkim należy zauważyć to, czy elementy najwyższego poziomu są widoczne w określonej kolejności. Na przykład:

- Większość właściwości grup i grupach definicji elementów występować po zaimportowaniu dla pliku Microsoft.Cpp.Default.props.

- Wszystkie elementy docelowe zostały zaimportowane na końcu pliku.

- Istnieje wiele grup właściwości, z których każda z unikatową etykietę i występują one w określonej kolejności.

Kolejność elementów w pliku projektu jest bardzo ważne, ponieważ program MSBuild jest oparty na modelu sekwencyjne oceny.  Jeśli plik projektu, w tym wszystkie zaimportowane, .props i .TARGETS, obejmuje wiele definicji właściwości, ostatnia definicja zastępuje te poprzedniego. W poniższym przykładzie wartość "ciągu xyz" zostanie ustawiona podczas kompilacji, ponieważ MSBUild aparatu napotka jej ostatniego podczas jej obliczania.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

Poniższy fragment kodu przedstawia plik .vcxproj minimalny. Dowolny plik .vcxproj generowane przez program Visual Studio będzie zawierać tych elementów MSBuild najwyższego poziomu i pojawią się one w następującej kolejności (chociaż mogą zawierać wiele kopii każdego elementu najwyższego poziomu). Należy pamiętać, że `Label` atrybuty są dowolne tagi, które są używane tylko przez program Visual Studio jako signposts do edycji, nie mają innych funkcji.

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

W poniższych sekcjach opisano przeznaczenia każdego z tych elementów i dlaczego są uporządkowane w ten sposób:

### <a name="project-element"></a>Project — element

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` jest węzłem głównym. Określa wersję programu MSBuild do użycia, a także domyślnego obiektu docelowego do wykonania, gdy ten plik jest przekazywany do MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations itemgroup — element

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` Zawiera opis konfiguracji projektu. Należą do nich debugowania | Win32, wydanie | Win32, debugowanie | ARM i tak dalej. Wiele ustawień projektu są specyficzne dla danej konfiguracji. Na przykład prawdopodobnie można ustawić właściwości optymalizacji dla kompilacji wydania, ale nie kompilacji debugowania.

`ProjectConfigurations` Grupa elementów nie jest używany w czasie kompilacji. Środowiska IDE programu Visual Studio wymagają, aby można było załadować projekt. Ta grupa może być przeniesiony do pliku, .props i importowane do plik .vcxproj. Jednak w takim przypadku, jeśli potrzebujesz dodać lub usunąć konfiguracje, należy ręcznie zmodyfikować plik .props; Nie można użyć środowiska IDE.

### <a name="projectconfiguration-elements"></a>Elementy ProjectConfiguration

Poniższy fragment kodu przedstawia konfigurację projektu. W tym przykładzie "Debug | x 64 jest nazwa konfiguracji. Nazwa konfiguracji projektu musi być w $(Configuration)|$(Platform). formatu Węzeł konfiguracji projektu może mieć dwie właściwości: Konfiguracja i platforma. Te właściwości zostaną ustawione automatycznie przy użyciu wartości określone w tym miejscu, gdy konfiguracja jest aktywny.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE spodziewa się znaleźć plik konfiguracyjny dla dowolnej kombinacji wartości Konfiguracja i platforma, które są używane we wszystkich elementach ProjectConfiguration. Często oznacza to, że projekt może mieć konfiguracje projektu bez znaczenia, aby spełnić to wymaganie. Na przykład jeśli projekt zawiera następujące konfiguracje:

- Debug|Win32

- Retail|Win32

- Specjalne optymalizacji 32-bitowych | Win32

następnie musi mieć również te konfiguracje, nawet jeśli "Specjalne optymalizacji 32-bitowy" jest całkowicie nieprzydatna x64:

- Debug|x64

- Retail|x64

- Specjalne optymalizacji 32-bitowych | x64

Można wyłączyć kompilacji i wdrażania poleceń dla żadnej konfiguracji w **Menedżerze konfiguracji rozwiązania**.

### <a name="globals-propertygroup-element"></a>Funkcje globalne PropertyGroup — element

```xml
<PropertyGroup Label="Globals" />
```

`Globals` zawiera ustawienia poziomu projektu, takich jak ProjectGuid RootNamespace i ApplicationType / ApplicationTypeRevision. Ostatnie dwa często definiują docelowego systemu operacyjnego. Projektu można kierować tylko jednego systemu operacyjnego, na fakt, że odniesienia i elementów projektu nie może mieć warunki obecnie. Te właściwości zwykle nie są zastępowane innym miejscu w pliku projektu. Ta grupa nie jest zależny od konfiguracji i dlatego zwykle istnieje tylko jedna globalne grupa w pliku projektu.

### <a name="microsoftcppdefaultprops-import-element"></a>Import pliku Microsoft.Cpp.default.props — element

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

**Pliku Microsoft.Cpp.default.props** arkusz właściwości jest dostarczany z programem Visual Studio i nie może być modyfikowany. Zawiera ustawienia domyślne dla projektu. Ustawienia domyślne mogą się różnić w zależności od ApplicationType.

### <a name="configuration-propertygroup-elements"></a>Elementy PropertyGroup konfiguracji

```xml
<PropertyGroup Label="Configuration" />
```

A `Configuration` grupy właściwości zawiera warunek dołączonych konfiguracji (takich jak `Condition=”'$(Configuration)|$(Platform)'=='Debug|Win32'”`) i jest dostępna w wielu kopii, po jednym w każdym konfiguracji. Ta grupa właściwość udostępnia właściwości, które są ustawiane dla określonej konfiguracji. Właściwości konfiguracji obejmują zestaw narzędzi platformy, a także kontrolować sposób włączenia systemu arkuszy właściwości w **pliku Microsoft.Cpp.props**. Na przykład, jeśli zdefiniowano właściwość `<CharacterSet>Unicode</CharacterSet>`, następnie systemowy arkusz właściwości **firmy microsoft. CPP.unicodesupport.props** zostaną dołączone. Jeśli możesz sprawdzić **pliku Microsoft.Cpp.props**, zostanie wyświetlony wiersz: `<Import Condition=”'$(CharacterSet)' == 'Unicode'”   Project=”$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props”/>`.

### <a name="microsoftcppprops-import-element"></a>Import pliku Microsoft.Cpp.props — element

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

**Pliku Microsoft.Cpp.props** arkusz właściwości (bezpośrednio lub za pośrednictwem Importy) definiuje wartości domyślne dla wielu właściwości specyficzne dla narzędzia, takie jak kompilator optymalizacji i poziom ostrzeżeń właściwości TypeLibraryName narzędzie MIDL właściwości i tak dalej. Importuje różnych arkusze właściwości systemu, oparte na właściwości konfiguracji, które są zdefiniowane w grupie właściwości bezpośrednio powyżej.

### <a name="extensionsettings-importgroup-element"></a>ExtensionSettings importgroup — element

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings` Grupa zawiera import dla arkuszy właściwości, które są częścią dostosowania kompilacji. Dostosowanie kompilacji jest definiowany przez maksymalnie trzy pliki: plik .targets, plik .props i pliku XML. Ta grupa importu zawiera polecenie importuje plik .props.

### <a name="propertysheets-importgroup-elements"></a>Importgroup — PropertySheets elementów

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets` Grupa zawiera import dla arkuszy właściwości. Są to arkuszy właściwości, które możesz dodać za pomocą widoku Menedżer właściwości w programie Visual Studio. Kolejność, w którym są wyświetlane te imports jest ważna i znajduje odzwierciedlenie w Menedżerze właściwości. Plik projektu zawiera zazwyczaj wiele wystąpień tego rodzaju grupy importu, jeden dla każdej konfiguracji projektu.

### <a name="usermacros-propertygroup-element"></a>UserMacros PropertyGroup — element

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` zawiera właściwości jest tworzona jako zmienne, które są używane do dostosowywania procesu kompilacji. Na przykład można zdefiniować makro użytkownika w ścieżce danych wyjściowych niestandardowego jest definiowana jako $(CustomOutputPath) i użyć go do zdefiniowania inne zmienne. Ta grupa właściwość przechowuje tych właściwości. Należy pamiętać, że w programie Visual Studio, ta grupa jest pusta w pliku projektu ponieważ Visual C++ nie obsługuje konfiguracji makra użytkownika. Makra użytkownika są obsługiwane w arkuszach właściwości.

### <a name="per-configuration-propertygroup-elements"></a>Elementy PropertyGroup — Konfiguracja

```xml
<PropertyGroup />
```

Istnieje wiele wystąpień tej grupy właściwości, jeden na konfiguracji w przypadku wszystkich konfiguracji projektu. Każda grupa właściwość musi mieć jeden warunek konfiguracji dołączone. Jeśli brakuje konfiguracji **właściwości projektu** okno dialogowe nie będzie działać poprawnie. W przeciwieństwie do powyższych grup właściwość ta nie ma etykietę. Ta grupa zawiera ustawienia konfiguracji na poziomie projektu. Te ustawienia mają zastosowanie do wszystkich plików, które są częścią grupy określony element. Definicja elementu dostosowania kompilacji metadanych jest inicjowana w tym miejscu.

PropertyGroup ten musi być późniejsza `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` oraz nie może być nie innych PropertyGroup bez etykiety przed nim (w przeciwnym razie edytowanie właściwości projektu nie będzie działać poprawnie).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Elementy ItemDefinitionGroup — na konfiguracji

```xml
<ItemDefinitionGroup />
```

Zawiera definicje elementu. Te należy wykonać te same reguły warunków jako elementy PropertyGroup bez etykiety na konfiguracji.

### <a name="itemgroup-elements"></a>Itemgroup — elementy

```xml
<ItemGroup />
```

Zawiera elementy (pliki źródłowe, itp.) w projekcie. Warunki nie są obsługiwane dla elementów projektu (czyli typów elementów, które są traktowane jako elementy projektu przez definicje zasad).

Metadane powinna mieć warunki konfiguracji dla każdej konfiguracji, nawet jeśli są takie same. Na przykład:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|Win32’">true</TreatWarningAsError>
    <TreatWarningAsError Condition="‘$(Configuration)|$(Platform)’==’Debug|x64’">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

Visual Studio C++ system projektu aktualnie nie obsługuje symboli wieloznacznych w elementach projektu.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

Visual Studio C++ system projektu aktualnie nie obsługuje makr w elementach projektu.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Odwołania są określone w ItemGroup i mają następujące ograniczenia:

- Odwołania nie obsługują warunki.

- Odwołuje się do metadanych nie obsługują warunki.

### <a name="microsoftcpptargets-import-element"></a>Microsoft.Cpp.targets Import — element

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Definiuje (bezpośrednio lub za pośrednictwem Importy) obiekty docelowe Visual C++, takie jak kompilacja, czyszczenie itd.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets importgroup — element

```xml
<ImportGroup Label="ExtensionTargets" />
```

Ta grupa zawiera import dla pliki docelowe dostosowania kompilacji.

## <a name="impact-of-incorrect-ordering"></a>Wpływ niepoprawnej kolejności

Środowiska IDE programu Visual Studio zależy od zainstalowanej projektu pliku, których kolejność opisanych powyżej. Na przykład po zdefiniowaniu wartość właściwości na stronach właściwości IDE ogólnie umieści definicji właściwości w grupie właściwości z pustą etykietę. Daje to gwarancję, że wartości domyślne w arkuszach właściwości systemu są zastępowane przez wartości zdefiniowanej przez użytkownika. Podobnie pliki docelowe są importowane na końcu, ponieważ korzystają z właściwości zdefiniowanych powyżej i ponieważ one zazwyczaj nie definiują właściwości, samodzielnie. Podobnie, arkusz właściwości użytkownika są importowane po arkuszach właściwości systemu (dołączonych przy użyciu **pliku Microsoft.Cpp.props**). Daje to gwarancję, że użytkownik może przesłonić wartości domyślne dołączonych za pomocą arkuszy właściwości systemu.

Jeśli plik .vcxproj nie jest zgodna z ten układ, wyniki kompilacji może nie być, czego oczekiwać. Na przykład jeśli przez pomyłkę importujesz systemowym arkuszem właściwości po arkuszach właściwości zdefiniowane przez użytkownika, ustawienia użytkownika zostaną zastąpione przez arkusze właściwości systemu.

Nawet środowiska czasu projektowania IDE zależy do pewnego stopnia poprawne kolejność elementów. Na przykład, jeśli nie ma pliku .vcxproj `PropertySheets` Importuj grupę IDE może nie być możliwe ustalenie, gdzie umieścić nowy arkusz właściwości utworzony w **Menedżer właściwości**. Może to spowodować, że arkusz użytkownika przesłaniana przez arkusz systemu. Mimo, że Algorytm heurystyczny używany przez środowisko IDE może tolerować niewielkie niespójności w układzie plik .vcxproj, zdecydowanie zalecane jest aby nie różni się od struktury przedstawiony we wcześniejszej części tego artykułu.

## <a name="how-the-ide-uses-element-labels"></a>Jak IDE używa etykiety elementu

W środowisku IDE, po ustawieniu **UseOfAtl** właściwości na stronie właściwości ogólnych, jest ona zapisywana w grupy właściwości konfiguracji w pliku projektu, podczas gdy **TargetName** właściwości w tej samej stronie właściwości są zapisywane do grupy właściwości bez etykiety na konfiguracji. Program Visual Studio wygląda informacji o tym, gdzie do zapisania każdej właściwości w pliku xml na stronie właściwości. Aby uzyskać **ogólne** strony właściwości (przy założeniu, masz angielską wersję programu Visual Studio 2019 Enterprise Edition), ten plik jest `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml`. Plik reguł XML strony właściwości definiuje statyczne informacje dotyczące reguły i jego właściwości. Jeden zestaw takich informacji jest preferowany pozycji właściwości reguły w pliku docelowym (plik, w którym zostanie zapisany jego wartość). Pozycja preferowane jest określony przez atrybut etykiety elementów pliku projektu.

## <a name="property-sheet-layout"></a>Układ arkusza właściwości

Poniższy fragment kodu XML jest minimalny układ pliku (.props) arkusza właściwości. Jest on podobny do plik vcxproj i funkcjonalność, .props elementów można wywnioskować na podstawie wcześniejszych dyskusji.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Aby utworzyć arkusz właściwości, skopiuj jeden z plikach .props w folderze VCTargets i zmodyfikuj go do własnych celów. Dla programu Visual Studio 2019 r Enterprise edition, jest domyślna ścieżka VCTargets `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets`.

## <a name="see-also"></a>Zobacz także

[Ustawianie właściwości kompilacji i kompilatora języka C++ w programie Visual Studio](../working-with-project-properties.md)<br/>
[Pliki XML strony właściwości](property-page-xml-files.md)
