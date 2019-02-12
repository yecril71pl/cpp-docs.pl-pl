---
title: Pliki zasobów (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: 65500644b70841f372edcc6911edefc6c7b9f432
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152693"
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)

> [!NOTE]
> W tym materiale dotyczy aplikacje pulpitu Windows. Aby uzyskać informacje dotyczące zasobów w aplikacji platformy uniwersalnej Windows, zobacz [Definiowanie zasobów aplikacji](/windows/uwp/app-resources/).
>
> Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).
>
> Ponieważ projekty w językach programowania .NET należy używać plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Termin "pliku zasobów" może odwoływać się do wielu typów plików, w tym:

- Plik skryptu (.rc) zasobów programu.

- Plik szablonu (.rct) zasobów.

- Pojedynczy zasób istniejące jako autonomiczny plik, takiego jak plik mapy bitowej, ikona lub kursor jest to określane w pliku .rc.

- Plik nagłówka, generowane przez środowisko programistyczne, na przykład Resource.h, który jest określany w pliku .rc.

Zasoby znajdują się również w [innych typów plików](../windows/editable-file-types-for-resources.md) takich jak pliki .exe i .dll, .res. Można pracować z zasobami i plikami zasobów z w ramach projektu i te, które nie są częścią bieżącego projektu. Może również współdziałać z plikami zasobów, które nie zostały utworzone w środowisku projektowym programu Visual Studio. Możesz na przykład:

- Praca z plikami zasobów zagnieżdżone i dołączane warunkowo.

- Aktualizowanie istniejących zasobów lub konwersji do formatu Visual C++.

- Importowanie lub eksportowanie zasobów graficznych do lub z bieżącego pliku zasobów.

- Obejmują udostępnione lub tylko do odczytu identyfikatorów (symbolom), których nie można zmodyfikować przez środowisko programistyczne.

- W pliku wykonywalnym (.exe), które nie wymagają do edycji (lub który nie powinien być edytowany) podczas bieżącego projektu, takich jak zasobów udostępnionych między kilka projektów zostaną umieszczone zasoby.

- Obejmują typy zasobów, które nie są obsługiwane przez środowisko programistyczne.

Możesz otworzyć następujących typów plików i edytowanie zasobów, które zawierają:

|Nazwa pliku|Opis|
|---------------|-----------------|
|.rc|Pliki skryptów zasobów.|
|.rct|Pliki szablonów zasobów.|
|.res|Pliki zasobów.|
|.resx|Zarządzanych plików zasobów.|
|.exe|Pliki wykonywalne.|
|.dll|Pliki bibliotek dołączanych dynamicznie.|
|.bmp, .ico, .dib i .cur|Pliki map bitowych, ikony, narzędzi i kursora.|

W środowisku Visual Studio współpracuje z i wpływa na pliki przedstawione w poniższej tabeli podczas sesji edytowania zasobów:

|Nazwa pliku|Opis|
|---------------|-----------------|
|Resource.h|Plik nagłówkowy generowane przez środowisko programistyczne; zawiera definicje symbolu. (Dołącz ten plik w kontroli źródła).|
|Filename.APS|Binarna wersja bieżącego pliku skryptu zasobów; używany do szybkiego ładowania.<br /><br /> Edytory zasobów nie bezpośrednio odczytywać pliki .rc lub resource.h. Kompilator zasobów kompiluje je na .aps pliki, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne. Jak zwykłym skompilować procesu, informacje, które nie jest symboliczne (na przykład komentarzy) jest pomijany w procesie kompilacji. Zawsze, gdy plik .aps pobiera synchronizację z pliku .rc, zostanie ponownie wygenerowany plik .rc (na przykład podczas zapisywania, Edytor zasobów zastąpi plików .rc i pliku resource.h). Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [tym zasobów w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md). (Zazwyczaj nie należy dołączać pliku .aps w kontroli źródła.)|
|.rc|Plik skryptu zasobu, który zawiera skrypt dla zasobów w bieżącym projekcie. Ten plik jest nadpisywany przez plik .aps przy każdym zapisywaniu. (Dołącz ten plik w kontroli źródła).|

W tej sekcji omówiono sposób:

- [Tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md)

- [Zarządzanie zasobami](../windows/how-to-copy-resources.md)

- [Dołączanie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md)

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

Aby otwarcie zasobu manifestu, wybierz z następujących czynności:

- Do edytora tekstów, za pomocą projektu Otwórz w programie **Eksploratora rozwiązań**, rozwiń węzeł **pliki zasobów** folder i kliknij dwukrotnie plik .manifest.

- Dla innego edytora w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .manifest i wybierz **Otwórz za pomocą...**  z menu skrótów. W **Otwórz za pomocą** okno dialogowe, określ edytora, o których chcesz użyć, a następnie wybierz pozycję **Otwórz**.

> [!NOTE]
> Może mieć tylko jeden zasób manifestu dla modułu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz także

[Edytory zasobów](../windows/resource-editors.md)<br/>
[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Menu i inne zasoby](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Kontrolki](../mfc/controls-mfc.md)<br/>