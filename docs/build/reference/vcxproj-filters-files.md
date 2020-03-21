---
title: Vcxproj. filters — pliki
ms.date: 09/25/2019
description: Użyj plików filtrów w projektach programu C++ Visual Studio, aby zdefiniować niestandardowe foldery logiczne dla plików w Eksplorator rozwiązań
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: bdf40708a70d841cb3d3144fa8fa73a71e9e9ef2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078278"
---
# <a name="vcxprojfilters-files"></a>Vcxproj. filters — pliki

Plik *filtrów* (\*. vcxproj. filters) to plik XML w formacie MSBuild, który znajduje się w folderze głównym projektu. Określa, które typy plików przechodzą do folderu logicznego w **Eksplorator rozwiązań**. Na poniższej ilustracji pliki *. cpp* znajdują się pod węzłem **pliki źródłowe** . pliki *. h* znajdują się pod węzłem **plików nagłówkowych** , a pliki *. ico* i *. RC* znajdują się w obszarze **pliki zasobów**. To położenie jest kontrolowane przez plik Filters.

![Foldery logiczne w Eksplorator rozwiązań](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Tworzenie niestandardowego pliku filtrów

Program Visual Studio automatycznie tworzy ten plik. W przypadku aplikacji klasycznych wstępnie zdefiniowane foldery logiczne (filtry) to: **pliki źródłowe**, **pliki nagłówkowe** i **pliki zasobów**. Inne typy projektów, takie jak platformy UWP, mogą mieć inny zestaw folderów domyślnych. Program Visual Studio automatycznie przypisuje znane typy plików do każdego folderu. Jeśli chcesz utworzyć filtr z niestandardową nazwą lub filtrem, który zawiera niestandardowe typy plików, możesz utworzyć własny plik filtrów w folderze głównym projektu lub w ramach istniejącego filtru. (**Odwołania** i **zależności zewnętrzne** to specjalne foldery, które nie uczestniczą w filtrowaniu).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje plik filtrów dla przykładu. Ma ona płaską hierarchię; Innymi słowy, nie ma zagnieżdżonych folderów logicznych. Węzeł `UniqueIdentifier` jest opcjonalny. Umożliwia interfejsom automatyzacji programu Visual Studio znalezienie filtru. `Extensions` jest również opcjonalny. Gdy nowy plik zostanie dodany do projektu, jest dodawany do filtru znajdującego się najwyżej przy użyciu pasującego rozszerzenia pliku. Aby dodać plik do określonego filtru, kliknij prawym przyciskiem myszy filtr i wybierz polecenie **Dodaj nowy element**.

`ItemGroup`, który zawiera węzły `ClInclude` jest tworzony podczas pierwszego uruchomienia projektu. W przypadku generowania własnych plików vcxproj upewnij się, że wszystkie elementy projektu mają również wpis w pliku Filters. Wartości w węźle `ClInclude` zastępują domyślne filtrowanie na podstawie rozszerzeń plików. W przypadku dodania nowego elementu do projektu przy użyciu programu Visual Studio IDE doda do pliku filtrów pojedynczy wpis pliku. Filtr nie jest automatycznie ponownie przypisywany w przypadku zmiany rozszerzenia pliku.

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

Aby utworzyć zagnieżdżone foldery logiczne, zadeklaruj wszystkie węzły w filtrach `ItemGroup` jak pokazano poniżej. Każdy węzeł podrzędny musi deklarować pełną ścieżkę logiczną do najwyższego elementu nadrzędnego. W poniższym przykładzie należy zadeklarować pustą `ParentFilter`, ponieważ odwołuje się do niej w późniejszych węzłach.

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
