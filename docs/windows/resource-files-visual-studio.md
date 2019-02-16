---
title: Pliki zasobów (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
helpviewer_keywords:
- resources [C++]
- .rc files [C++]
- resource files [C++]
- resource script files [C++]
- resource script files [C++], Win-32 based applications
- resource script files [C++], files updated when editing resources
- resources [C++], types of resource files
- rct files [C++]
- rc files [C++]
- resource files [C++], types of
- .rct files [C++]
- resource script files [C++], unsupported types
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
- file types [C++], for resources
- resources [C++], editing
- files [C++], editable types
- resource editing
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
ms.openlocfilehash: 4d56a62dfa350b3113a28355433130563464c6be
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320539"
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)

> [!NOTE]
> Ponieważ projekty w językach programowania .NET należy używać plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Termin "pliku zasobów" może odwoływać się do wielu typów plików, w tym:

- Plik skryptu (.rc) zasobów programu.

- Plik szablonu (.rct) zasobów.

- Pojedynczy zasób istniejące jako autonomiczny plik, takiego jak plik mapy bitowej, ikona lub kursor jest to określane w pliku .rc.

- Plik nagłówka, generowane przez środowisko programistyczne, na przykład Resource.h, który jest określany w pliku .rc.

Zasoby znajdują się również w przypadku innych typów plików, takich jak pliki .res, .exe i .dll. Można pracować z zasobami i plikami zasobów z w ramach projektu i te, które nie są częścią bieżącego projektu. Może również współdziałać z plikami zasobów, które nie zostały utworzone w środowisku projektowym programu Visual Studio. Możesz na przykład:

- Praca z plikami zasobów zagnieżdżone i dołączane warunkowo.

- Aktualizowanie istniejących zasobów lub konwersji do formatu Visual C++.

- Importowanie lub eksportowanie zasobów graficznych do lub z bieżącego pliku zasobów.

- Obejmują udostępnione lub tylko do odczytu identyfikatorów (symbolom), których nie można zmodyfikować przez środowisko programistyczne.

- W pliku wykonywalnym (.exe), które nie wymagają do edycji (lub który nie powinien być edytowany) podczas bieżącego projektu, takich jak zasobów udostępnionych między kilka projektów zostaną umieszczone zasoby.

- Obejmują typy zasobów, które nie są obsługiwane przez środowisko programistyczne.

W tej sekcji omówiono sposób:

- [Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md)

- [Zarządzanie zasobami](../windows/how-to-copy-resources.md)

- [Dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md)

## <a name="editable-resource-file-types"></a>Typy plików zasobów można edytować

Następujące typy plików można otworzyć do edycji zasobów, które zawierają:

|Nazwa pliku|Opis|
|---------|-----------------|
|.rc|Pliki skryptów zasobów|
|.rct|Pliki szablonów zasobów|
|.res|Pliki zasobów|
|.resx|Zarządzanych plików zasobów|
|.exe|Pliki wykonywalne|
|.dll|Pliki bibliotek dołączanych dynamicznie|
|.bmp, .ico, .dib i .cur|Pliki map bitowych, ikony, narzędzi i kursora.|

W środowisku Visual Studio współpracuje z i ma wpływ na następujące pliki podczas sesji edytowania zasobu:

|Nazwa pliku|Opis|
|---------------|-----------------|
|Resource.h|Plik nagłówkowy generowane przez środowisko programistyczne; zawiera definicje symbolu. (Dołącz ten plik w kontroli źródła).|
|Filename.APS|Binarna wersja bieżącego pliku skryptu zasobów; używany do szybkiego ładowania.<br /><br /> Edytory zasobów nie bezpośrednio odczytywać pliki .rc lub resource.h. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [obejmujące zasoby w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md). (Zazwyczaj nie należy dołączać pliku .aps w kontroli źródła.)|
|.rc|Plik skryptu zasobu, który zawiera skrypt dla zasobów w bieżącym projekcie. Ten plik jest nadpisywany przez plik .aps przy każdym zapisywaniu. (Dołącz ten plik w kontroli źródła).|

## <a name="manifest-resources"></a>Zasoby manifestu

W projektach pulpitu C++ manifestu zasoby są plikami XML, które opisują zależności, których używa aplikacja. Na przykład w programie Visual Studio, plik manifestu generowane przez kreatora MFC definiuje, której wersji 5.0 lub 6.0, Windows formantu typowego bibliotek DLL, należy użyć aplikacji:

```xml
<description>Your app description here</description>
<dependency>
    <dependentAssembly>
        <assemblyIdentity
            type="win32"
            name="Microsoft.Windows.Common-Controls"
            version="6.0.0.0"
            processorArchitecture="X86"
            publicKeyToken="6595b64144ccf1df"
            language="*"
        />
    </dependentAssembly>
</dependency>
```

W przypadku aplikacji Windows XP lub Windows Vista zasobu manifestu określa nie tylko aplikacji, użyj najnowszej wersji Windows wspólnych formantów, w wersji 6.0, jak pokazano powyżej, że obsługuje ona również [kontroli Syslink](/windows/desktop/Controls/syslink-overview).

Aby wyświetlić wersję i typ informacji zawartych w zasobu manifestu, można otworzyć go w podglądzie XML lub Edytor tekstu Visual Studio. Jeśli otwarcie zasobu manifestu z [widok zasobów](../windows/resource-view-window.md), zasób zostanie otwarty w formacie binarnym. Aby wyświetlić zawartość zasobu manifestu w postaci bardziej widoczne, należy otworzyć zasób z **Eksploratora rozwiązań**.

### <a name="to-open-a-manifest-resource"></a>Aby otworzyć zasobu manifestu

1. Otwórz swój projekt w programie Visual Studio.

1. Przejdź do **Eksploratora rozwiązań** i rozwiń **pliki zasobów** folderu.

   - Edytor tekstu kliknij dwukrotnie plik .manifest.

   - Dla innych edytorów, kliknij prawym przyciskiem myszy plik .manifest, a następnie wybierz pozycję **Otwórz za pomocą...** , następnie określ edytora, aby użyć, a następnie wybierz **Otwórz**.

> [!NOTE]
> Może mieć tylko jeden zasób manifestu dla modułu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Identyfikatory zasobów (symbolom)](../windows/symbols-resource-identifiers.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>