---
title: Struktura plików vcxproj i props
description: Jak natywne pliki Project System. vcxproj i. props języka C++ przechowują informacje o projekcie.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 562ef0c1b371d7212f31da1917d19c012e4cbb24
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662285"
---
# <a name="vcxproj-and-props-file-structure"></a>`.vcxproj` i `.props` Struktura plików

[MSBuild](../msbuild-visual-cpp.md) jest domyślnym systemem projektu w programie Visual Studio; Po wybraniu opcji **plik**  >  **Nowy projekt** w Visual C++ tworzysz projekt programu MSBuild, którego ustawienia są przechowywane w pliku projektu XML, który ma rozszerzenie *`.vcxproj`* . Plik projektu może również importować *`.props`* pliki i pliki, w *`.targets`* których można przechowywać ustawienia.

Zalecamy tworzenie i modyfikowanie *`.vcxproj`* projektów w IDE oraz uniknięcie ręcznej edycji. W większości przypadków nie trzeba ręcznie edytować pliku projektu. Za każdym razem, gdy to możliwe, należy użyć stron właściwości programu Visual Studio do modyfikowania ustawień projektu. Aby uzyskać więcej informacji, zobacz [Ustawianie kompilatora C++ i właściwości kompilacji w programie Visual Studio](../working-with-project-properties.md).

Jeśli potrzebujesz dostosowań, które nie są możliwe w środowisku IDE, zalecamy dodanie niestandardowych właściwości lub obiektów docelowych. Przydatne miejsca do wstawiania dostosowań to *`Directory.Build.props`* *`Directory.Build.targets`* pliki i, które są automatycznie importowane we wszystkich projektach opartych na programie MSBuild.

W niektórych przypadkach nadal trzeba *`.vcxproj`* ręcznie zmodyfikować plik projektu lub arkusz właściwości. Nie zalecamy edytowania go ręcznie, chyba że masz dobre zrozumienie programu MSBuild i postępuj zgodnie z wytycznymi z tego artykułu. Aby środowisko IDE mogło automatycznie ładować i aktualizować *`.vcxproj`* pliki, te pliki mają kilka ograniczeń, które nie mają zastosowania do innych plików projektów programu MSBuild. Nie zostały one zaprojektowane do edycji ręcznej. Błędy mogą spowodować awarię lub zachowanie środowiska IDE w nieoczekiwany sposób.

W przypadku scenariuszy ręcznej edycji ten artykuł zawiera podstawowe informacje o strukturze *`.vcxproj`* i powiązanych plikach.

**Ważne:**

Jeśli zdecydujesz się edytować *`.vcxproj`* plik ręcznie, weź pod uwagę następujące fakty:

- Struktura pliku musi być zgodna z określonym formularzem, który opisano w tym artykule.

- System projektu Visual Studio C++ obecnie nie obsługuje symboli wieloznacznych ani list bezpośrednio w elementach projektu. Na przykład te formularze nie są obsługiwane:

   ```xml
   <ItemGroup>
     <None Include="*.txt"/>
     <ClCompile Include="a.cpp;b.cpp"/>
   </ItemGroup>
   ```

   Aby uzyskać więcej informacji na temat obsługi symboli wieloznacznych w projektach i możliwych obejść, zobacz [ `.vcxproj` pliki i symbole wieloznaczne](vcxproj-files-and-wildcards.md).

- System projektu Visual Studio C++ obecnie nie obsługuje makr w ścieżkach elementów projektu. Na przykład ten formularz nie jest obsługiwany:

   ```xml
   <ItemGroup>
     <ClCompile Include="$(IntDir)\generated.cpp"/>
   </ItemGroup>
   ```

   "Nieobsługiwane" oznacza, że makra nie są gwarantowane do pracy w przypadku wszystkich operacji w IDE. Makra, które nie zmieniają ich wartości w różnych konfiguracjach, powinny działać, ale mogą nie być zachowywane, jeśli element zostanie przeniesiony do innego filtru lub projektu. Makra, które zmieniają ich wartości dla różnych konfiguracji, spowodują problemy. Dzieje się tak, ponieważ IDE nie oczekuje, że ścieżki elementów projektu różnią się w zależności od konfiguracji projektu.

- Aby dodać, usunąć lub zmodyfikować właściwości projektu, gdy edytujesz je w oknie dialogowym **właściwości projektu** , plik musi zawierać osobne grupy dla każdej konfiguracji projektu. Warunki muszą mieć następującą formę:

   ```xml
   Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"
   ```

- Każda właściwość musi być określona w grupie ze swoją poprawną etykietą, jak określono w pliku reguły właściwości. Aby uzyskać więcej informacji, zobacz [pliki reguł XML na stronie właściwości](property-page-xml-files.md).

## <a name="vcxproj-file-elements"></a>`.vcxproj` elementy pliku

Zawartość pliku można sprawdzić przy *`.vcxproj`* użyciu dowolnego edytora tekstu lub XML. Możesz wyświetlić go w programie Visual Studio, klikając prawym przyciskiem myszy projekt w Eksplorator rozwiązań, wybierając pozycję **Zwolnij projekt** , a następnie wybierając pozycję **Edytuj foo. vcxproj**.

Pierwszy należy zauważyć, że elementy najwyższego poziomu pojawiają się w określonej kolejności. Przykład:

- Większość grup właściwości i grup definicji elementów występuje po imporcie dla elementu Microsoft. cpp. default. props.

- Wszystkie elementy docelowe są importowane na końcu pliku.

- Istnieje wiele grup właściwości, z których każda ma unikatową etykietę i pojawia się w określonej kolejności.

Kolejność elementów w pliku projektu jest istotna, ponieważ program MSBuild jest oparty na modelu oceny sekwencyjnej.  Jeśli plik projektu, w tym wszystkie zaimportowane *`.props`* i *`.targets`* pliki, składa się z wielu definicji właściwości, ostatnia definicja zastępuje poprzednią. W poniższym przykładzie wartość "XYZ" zostanie ustawiona podczas kompilacji, ponieważ aparat MSBUild napotka go jako ostatni podczas jego oceny.

```xml
  <MyProperty>abc</MyProperty>
  <MyProperty>xyz</MyProperty>
```

Poniższy fragment kodu przedstawia minimalny *`.vcxproj`* plik. Każdy *`.vcxproj`* plik wygenerowany przez program Visual Studio będzie zawierać te elementy programu MSBuild najwyższego poziomu. I, pojawią się w tej kolejności, ale mogą zawierać wiele kopii każdego takiego elementu najwyższego poziomu. Wszystkie `Label` atrybuty są dowolnymi tagami, które są używane przez program Visual Studio jako oznaki do edycji; nie mają żadnej innej funkcji.

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

W poniższych sekcjach opisano przeznaczenie każdego z tych elementów i przyczyny ich uporządkowania:

### <a name="project-element"></a>Project, element

```xml
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns='http://schemas.microsoft.com/developer/msbuild/2003' >
```

`Project` jest węzłem głównym. Określa wersję programu MSBuild, która ma być używana, a także domyślny cel do wykonania, gdy ten plik zostanie przesłany do MSBuild.exe.

### <a name="projectconfigurations-itemgroup-element"></a>ProjectConfigurations element elementu

```xml
<ItemGroup Label="ProjectConfigurations" />
```

`ProjectConfigurations` zawiera opis konfiguracji projektu. Przykłady są debugowaniem | Win32, wydanie | Win32, Debuguj | ARM i tak dalej. Wiele ustawień projektu jest specyficznych dla danej konfiguracji. Na przykład prawdopodobnie zechcesz ustawić właściwości optymalizacji dla kompilacji wydania, ale nie na kompilację debugowania.

`ProjectConfigurations`Grupa elementów nie jest używana w czasie kompilacji. Środowisko IDE programu Visual Studio wymaga załadowania projektu. Ta grupa elementów może zostać przeniesiona do *`.props`* pliku i zaimportowana do *`.vcxproj`* pliku. Jednak w takim przypadku, jeśli trzeba dodać lub usunąć konfiguracje, należy ręcznie edytować *`.props`* plik. nie można używać środowiska IDE.

### <a name="projectconfiguration-elements"></a>Elementy ProjectConfiguration

Poniższy fragment kodu przedstawia konfigurację projektu. W tym przykładzie "Debugowanie | x64" jest nazwą konfiguracji. Nazwa konfiguracji projektu musi być w formacie `$(Configuration)|$(Platform)` . `ProjectConfiguration`Węzeł może mieć dwie właściwości: `Configuration` i `Platform` . Te właściwości są ustawiane automatycznie przy użyciu wartości określonych w tym miejscu, gdy konfiguracja jest aktywna.

```xml
<ProjectConfiguration Include="Debug|x64">
  <Configuration>Debug</Configuration>
  <Platform>x64</Platform>
</ProjectConfiguration>
```

IDE oczekuje na znalezienie konfiguracji projektu dla dowolnej kombinacji `Configuration` i `Platform` wartości używanych we wszystkich `ProjectConfiguration` elementach. Często oznacza to, że projekt może mieć bez znaczenia konfiguracje projektu, aby spełnić to wymaganie. Na przykład, jeśli projekt ma następujące konfiguracje:

- Debuguj | System

- Sprzedaż detaliczna | System

- Specjalna 32-bitowa Optymalizacja | System

następnie musi również mieć te konfiguracje, chociaż "Specjalna Optymalizacja 32-bitowa" ma znaczenie dla architektury x64:

- Debuguj | x64

- Sprzedaż detaliczna | x64

- Specjalna 32-bitowa Optymalizacja | x64

Polecenia Kompiluj i Wdróż można wyłączyć dla każdej konfiguracji w **Configuration Manager rozwiązania**.

### <a name="globals-propertygroup-element"></a>Globals — element właściwości

```xml
<PropertyGroup Label="Globals" />
```

`Globals` zawiera ustawienia na poziomie projektu, takie jak `ProjectGuid` , `RootNamespace` i `ApplicationType` lub `ApplicationTypeRevision` . Ostatnie dwa często definiują docelowy system operacyjny. Projekt może być przeznaczony tylko dla jednego systemu operacyjnego, ponieważ obecnie odwołania i elementy projektu nie mogą mieć warunków. Te właściwości nie są zwykle zastępowane w innym miejscu w pliku projektu. Ta grupa nie jest zależna od konfiguracji i zazwyczaj istnieje tylko jedna `Globals` Grupa w pliku projektu.

### <a name="microsoftcppdefaultprops-import-element"></a>Microsoft. cpp. default. props — element importu

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
```

Arkusz właściwości **Microsoft. cpp. default. props** jest dostarczany z programem Visual Studio i nie można go modyfikować. Zawiera ustawienia domyślne dla projektu. Wartości domyślne mogą się różnić w zależności od typu ApplicationType.

### <a name="configuration-propertygroup-elements"></a>Elementy właściwości konfiguracji

```xml
<PropertyGroup Label="Configuration" />
```

`Configuration`Grupa właściwości ma dołączony warunek konfiguracji (na przykład `Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'"` ) i znajduje się w wielu kopiach, jeden na konfigurację. Ta grupa właściwości zawiera właściwości, które są ustawione dla określonej konfiguracji. Właściwości konfiguracji obejmują PlatformToolset oraz kontrolują dołączenie systemowych arkuszy właściwości do **Microsoft. cpp. props**. Na przykład, jeśli zdefiniujesz Właściwość `<CharacterSet>Unicode</CharacterSet>` , to systemowy arkusz właściwości **Microsoft. Zostaną uwzględnione cpp. unicodesupport. props** . W przypadku inspekcji **Microsoft. cpp. props**zobaczysz wiersz: `<Import Condition="'$(CharacterSet)' == 'Unicode'" Project="$(VCTargetsPath)\microsoft.Cpp.unicodesupport.props" />` .

### <a name="microsoftcppprops-import-element"></a>Microsoft. cpp. props — element importu

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
```

Arkusz właściwości **Microsoft. cpp. props** (bezpośrednio lub za pośrednictwem importu) definiuje wartości domyślne dla wielu właściwości specyficznych dla narzędzia. Przykłady obejmują właściwości optymalizacji i poziomu ostrzeżeń kompilatora, właściwość TypeLibraryName narzędzia MIDL i tak dalej. Importuje również różne systemowe arkusze właściwości na podstawie tego, które właściwości konfiguracji są zdefiniowane bezpośrednio w grupie właściwości.

### <a name="extensionsettings-importgroup-element"></a>Poprawny ExtensionSettings element obiektu

```xml
<ImportGroup Label="ExtensionSettings" />
```

`ExtensionSettings`Grupa zawiera Importy dla arkuszy właściwości, które są częścią dostosowania kompilacji. Dostosowanie kompilacji jest definiowane przez maksymalnie trzy pliki: *`.targets`* plik, *`.props`* plik i *`.xml`* plik. Ta grupa importu zawiera Importy dla tego *`.props`* pliku.

### <a name="propertysheets-importgroup-elements"></a>PropertySheets elementy obiektu

```xml
<ImportGroup Label="PropertySheets" />
```

`PropertySheets`Grupa zawiera operacje importowania arkuszy właściwości użytkownika. Te Importy są arkuszami właściwości, które można dodać za pomocą widoku Menedżer właściwości w programie Visual Studio. Kolejność, w której wymienione są te Importy, jest ważna i jest odzwierciedlana w Menedżer właściwości. Plik projektu zwykle zawiera wiele wystąpień tego rodzaju grupy importowania, po jednej dla każdej konfiguracji projektu.

### <a name="usermacros-propertygroup-element"></a>UserMacros — element właściwości

```xml
<PropertyGroup Label="UserMacros" />
```

`UserMacros` zawiera właściwości, które tworzysz jako zmienne, które są używane do dostosowywania procesu kompilacji. Na przykład można zdefiniować makro użytkownika, aby zdefiniować niestandardową ścieżkę wyjściową jako $ (CustomOutputPath) i użyć jej do zdefiniowania innych zmiennych. Ta grupa właściwości przechowuje takie właściwości. W programie Visual Studio ta grupa nie jest wypełniana w pliku projektu, ponieważ Visual C++ nie obsługuje makr użytkownika dla konfiguracji. Makra użytkownika są obsługiwane w arkuszach właściwości.

### <a name="per-configuration-propertygroup-elements"></a>Elementy właściwości dla każdej konfiguracji

```xml
<PropertyGroup />
```

Istnieje wiele wystąpień tej grupy właściwości, jedną dla każdej konfiguracji dla wszystkich konfiguracji projektu. Każda grupa właściwości musi mieć dołączony jeden warunek konfiguracji. W przypadku braku konfiguracji okno dialogowe **właściwości projektu** nie będzie działało poprawnie. W przeciwieństwie do grup właściwości wymienionych wcześniej, ten element nie ma etykiety. Ta grupa zawiera ustawienia na poziomie konfiguracji projektu. Te ustawienia mają zastosowanie do wszystkich plików, które są częścią określonej grupy elementów. Metadane definicji elementu dostosowania kompilacji są inicjowane w tym miejscu.

Ta właściwość musi znajdować `<Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />` się po i nie może istnieć żadna inna Właściwość bez etykiety (w przeciwnym razie Edytowanie właściwości projektu nie będzie działać poprawnie).

### <a name="per-configuration-itemdefinitiongroup-elements"></a>Elementy ItemDefinitionGroup na konfigurację

```xml
<ItemDefinitionGroup />
```

Zawiera definicje elementów. Te definicje muszą być zgodne z tymi samymi regułami co elementy w poszczególnych konfiguracjach `PropertyGroup` .

### <a name="itemgroup-elements"></a>Elementy elementu

```xml
<ItemGroup />
```

`ItemGroup` elementy zawierają elementy (pliki źródłowe itd.) w projekcie. Warunki nie są obsługiwane dla elementów projektu (oznacza to, że typy elementów, które są traktowane jako elementy projektu według definicji reguł).

Metadane powinny mieć warunki konfiguracji dla każdej konfiguracji, nawet jeśli są takie same. Przykład:

```xml
<ItemGroup>
  <ClCompile Include="stdafx.cpp">
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">true</TreatWarningAsError>
    <TreatWarningAsError Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">true</TreatWarningAsError>
  </ClCompile>
</ItemGroup>
```

System projektu Visual Studio C++ obecnie nie obsługuje symboli wieloznacznych w elementach projektu.

```xml
<ItemGroup>
  <ClCompile Include="*.cpp"> <!--Error-->
</ItemGroup>
```

System projektu Visual Studio C++ obecnie nie obsługuje makr w elementach projektu.

```xml
<ItemGroup>
  <ClCompile Include="$(IntDir)\generated.cpp"> <!--not guaranteed to work in all scenarios-->
</ItemGroup>
```

Odwołania są określone w elemencie Items i mają następujące ograniczenia:

- Odwołania nie obsługują warunków.

- Metadane odwołań nie obsługują warunków.

### <a name="microsoftcpptargets-import-element"></a>Element Imports Microsoft. cpp. targets

```xml
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
```

Definiuje (bezpośrednio lub poprzez import) cele języka C++, takie jak kompilacja, czyszczenie i tak dalej.

### <a name="extensiontargets-importgroup-element"></a>ExtensionTargets element obiektu

```xml
<ImportGroup Label="ExtensionTargets" />
```

Ta grupa zawiera Importy dla plików docelowych dostosowywania kompilacji.

## <a name="impact-of-incorrect-ordering"></a>Wpływ nieprawidłowej kolejności

Środowisko IDE programu Visual Studio jest zależne od pliku projektu, który ma opisane wcześniej kolejność. Na przykład po zdefiniowaniu wartości właściwości na stronach właściwości środowisko IDE zazwyczaj umieści definicję właściwości w grupie właściwości z pustą etykietą. Takie porządkowanie zapewnia, że wartości domyślne wprowadzone w arkuszach właściwości systemu są zastępowane przez wartości zdefiniowane przez użytkownika. Podobnie pliki docelowe są importowane na końcu, ponieważ korzystają z właściwości zdefiniowanych przed, i ponieważ zazwyczaj nie definiują samych właściwości. Podobnie arkusze właściwości użytkownika są importowane po arkuszu właściwości systemu (zawarte przez *`Microsoft.Cpp.props`* ). Ta kolejność zapewnia, że użytkownik może zastąpić wszystkie wartości domyślne, które są wprowadzane przez systemowe arkusze właściwości.

Jeśli *`.vcxproj`* plik nie jest zgodny z tym układem, wyniki kompilacji mogą nie być oczekiwane. Na przykład w przypadku błędnego zaimportowania systemowego arkusza właściwości po arkuszu właściwości zdefiniowanym przez użytkownika ustawienia użytkownika zostaną przesłonięte przez systemowe arkusze właściwości.

Nawet czas projektowania środowiska IDE zależy od pewnego zakresu od prawidłowego uporządkowania elementów. Na przykład jeśli *`.vcxproj`* plik nie ma `PropertySheets` grupy importowania, środowisko IDE może nie być w stanie określić, gdzie umieścić nowy arkusz właściwości utworzony przez użytkownika w **Menedżer właściwości**. Może to spowodować, że arkusz użytkownika zostanie przesłonięty przez arkusz systemowy. Chociaż algorytm heurystyczny używany przez IDE może tolerować niewielkie niespójności w *`.vcxproj`* układzie pliku, zdecydowanie zalecamy, aby nie odróżnić od struktury pokazanej wcześniej w tym artykule.

## <a name="how-the-ide-uses-element-labels"></a>Jak środowisko IDE używa etykiet elementów

W środowisku IDE, gdy właściwość **UseOfAtl** jest ustawiana na stronie właściwości ogólne, jest zapisywana w grupie Właściwości konfiguracji w pliku projektu. Właściwość **TargetName** znajdująca się na tej samej stronie właściwości jest zapisywana w grupie Właściwości "Less" na etykiecie. Program Visual Studio analizuje plik XML strony właściwości, aby uzyskać informacje o tym, gdzie należy napisać każdą właściwość. Na stronie właściwości **Ogólne** , przy założeniu, że masz angielską wersję programu Visual Studio 2019 Enterprise Edition, ten plik jest `%ProgramFiles(x86)%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets\1033\general.xml` . Plik reguł XML strony właściwości definiuje statyczne informacje o regule i jej właściwości. Jedną z tych informacji jest preferowane położenie właściwości reguły w pliku docelowym (plik, w którym zostanie zapisywana jego wartość). Preferowana pozycja jest określana przez atrybut Label dla elementów pliku projektu.

## <a name="property-sheet-layout"></a>Układ arkusza właściwości

Poniższy fragment kodu XML jest minimalnym układem pliku arkusza właściwości (. props). Jest on podobny do *`.vcxproj`* pliku, a funkcjonalność *`.props`* elementów można wywnioskować na podstawie wcześniejszej dyskusji.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ImportGroup Label="PropertySheets" />
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup />
  <ItemDefinitionGroup />
  <ItemGroup />
</Project>
```

Aby utworzyć własny arkusz właściwości, skopiuj jeden z *`.props`* plików w *`VCTargets`* folderze i zmodyfikuj go do swoich celów. W przypadku programu Visual Studio 2019 Enterprise Edition *`VCTargets`* ścieżka domyślna to `%ProgramFiles%\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\VC\VCTargets` .

## <a name="see-also"></a>Zobacz też

[Ustawianie właściwości kompilatora i kompilacji języka C++ w programie Visual Studio](../working-with-project-properties.md)\
[Pliki XML strony właściwości](property-page-xml-files.md)\
[`.vcxproj` pliki i symbole wieloznaczne](vcxproj-files-and-wildcards.md)
