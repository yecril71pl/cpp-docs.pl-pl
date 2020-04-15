---
title: Pliki Vcxproj.filters
ms.date: 09/25/2019
description: Definiowanie niestandardowych folderów logicznych dla plików w Eksploratorze rozwiązań za pomocą plików filtrów w projektach programu Visual Studio C++
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335931"
---
# <a name="vcxprojfilters-files"></a>pliki vcxproj.filters

Plik *filtrów* \*(.vcxproj.filters) jest plikiem XML w formacie MSBuild, który znajduje się w głównym folderze projektu. Określa, które typy plików przechodzą do którego folderu logicznego w **Eksploratorze rozwiązań**. Na poniższej ilustracji pliki *.cpp* znajdują się w węźle **Pliki źródłowe.** pliki *.h* znajdują się w węźle **Pliki nagłówka,** a pliki *.ico* i *.rc* znajdują się w obszarze **Pliki zasobów**. To umieszczenie jest kontrolowane przez plik filtrów.

![Foldery logiczne w Eksploratorze rozwiązań](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Tworzenie pliku filtrów niestandardowych

Program Visual Studio automatycznie tworzy ten plik. W przypadku aplikacji klasycznych wstępnie zdefiniowane foldery logiczne (filtry) to: **Pliki źródłowe,** **Pliki nagłówkowe** i **Pliki zasobów**. Inne typy projektów, takie jak platformy uniwersalne systemu Windows, mogą mieć inny zestaw folderów domyślnych. Program Visual Studio automatycznie przypisuje znane typy plików do każdego folderu. Aby utworzyć filtr o niestandardowej nazwie lub filtr zawierający niestandardowe typy plików, można utworzyć własny plik filtrów w folderze głównym projektu lub w istniejącym filtrze. (Odwołania i **zależności zewnętrzne** to specjalne foldery, które nie uczestniczą w filtrowaniu).**References**

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano plik filtrów dla przykładu pokaż wcześniej. Ma płaską hierarchię; innymi słowy, nie ma zagnieżdżonych folderów logicznych. Węzeł `UniqueIdentifier` jest opcjonalny. Umożliwia interfejsom automatyzacji programu Visual Studio, aby znaleźć filtr. `Extensions`jest również opcjonalna. Po dodaniu nowego pliku do projektu jest on dodawany do filtru najwyższego z pasującym rozszerzeniem pliku. Aby dodać plik do określonego filtru, kliknij prawym przyciskiem myszy filtr i wybierz polecenie **Dodaj nowy element**.

Zawiera `ItemGroup` węzły `ClInclude` jest tworzony podczas pierwszego uruchomienia projektu. Jeśli generujesz własne pliki vcxproj, upewnij się, że wszystkie elementy projektu mają również wpis w pliku filtrów. Wartości w `ClInclude` węźle zastępują domyślne filtrowanie na podstawie rozszerzeń plików. Podczas korzystania z programu Visual Studio, aby dodać nowy element do projektu, IDE doda pojedynczy wpis pliku w pliku filtrów. Filtr nie zostanie automatycznie przypisany ponownie po zmianie rozszerzenia pliku.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

Aby utworzyć zagnieżdżone foldery logiczne, należy zadeklarować wszystkie węzły w filtrach, `ItemGroup` jak pokazano poniżej. Każdy węzeł podrzędny musi zadeklarować pełną ścieżkę logiczną do najwyższego nadrzędnego. W poniższym przykładzie `ParentFilter` pusty musi być zadeklarowany, ponieważ odwołuje się do niego w późniejszych węzłach.

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```
