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
ms.openlocfilehash: bd73db481659573d51e4abd56da9689e2e8ade25
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676438"
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)

> [!NOTE]
> Ponieważ projekty w językach programowania .NET należy używać plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Użyj [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych.
>
> Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Termin *pliku zasobów* mogą odwoływać się do wielu typów plików, takie jak:

- Plik skryptu (.rc) zasobów programu.

- Plik szablonu (.rct) zasobów.

- Pojedynczy zasób istniejące jako autonomiczny plik. Ten typ zawiera plik mapy bitowej, ikona lub kursor jest określane w pliku .rc.

- Plik nagłówka, generowane przez środowisko programistyczne. Ten typ obejmuje `Resource.h`, jest to określane w pliku .rc.

Znaleziono zasobów w przypadku innych typów plików, takich jak pliki .exe i .dll, .res są określane jako *zasobów*.

Możesz pracować z *pliki zasobów* i *zasobów* z w obrębie projektu. Możesz także pracować z tymi, które nie są częścią bieżącego projektu lub zostały utworzone poza środowiskiem projektowania programu Visual Studio. Możesz na przykład:

- Praca z plikami zasobów zagnieżdżone i dołączane warunkowo.

- Aktualizowanie istniejących zasobów lub też przekonwertować je do programu Visual C++.

- Importowanie lub eksportowanie zasobów graficznych do lub z bieżącego pliku zasobów.

- Obejmują udostępnione lub tylko do odczytu identyfikatorów (symbolom), których nie można zmodyfikować przez środowisko programistyczne.

- W pliku wykonywalnym (.exe), które nie wymagają do edycji (lub nie powinny być edytowane), takie jak zasobów udostępnionych między kilka projektów zostaną umieszczone zasoby.

- Obejmują typy zasobów, które nie są obsługiwane przez środowisko programistyczne.

Aby uzyskać więcej informacji na temat zasobów, zobacz instrukcje [tworzenie zasobów](../windows/how-to-create-a-resource-script-file.md), [zarządzanie zasobami](../windows/how-to-copy-resources.md), i [obejmujące zasoby w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Można edytować zasoby.

Następujące typy plików można otworzyć do edycji zasobów, które zawierają:

| Nazwa pliku | Opis |
|---|---|
| .rc | Pliki skryptów zasobów |
| .rct | Pliki szablonów zasobów |
| .res | Pliki zasobów |
| .resx | Zarządzanych plików zasobów |
| .exe | Pliki wykonywalne |
| .dll | Pliki bibliotek dołączanych dynamicznie |
| .bmp .ico, .dib, .cur | Pliki map bitowych, ikony, narzędzi i kursora |

Podczas edytowania zasobów, w środowisku Visual Studio współpracuje z i ma wpływ na następujące pliki:

| Nazwa pliku | Opis |
|---|---|
| Resource.h | Plik nagłówkowy generowane przez środowisko programistyczne, która zawiera definicje symbolu.<br/><br/>Uwzględnij ten plik w kontroli źródła. |
| Filename.APS | Binarna wersja bieżącego pliku skryptu zasobów używany do szybkiego ładowania.<br /><br /> Edytory zasobów nie bezpośrednio odczytywać pliki .rc lub resource.h. Kompilator zasobów kompiluje je na pliki .aps, które są używane przez edytory zasobów. Ten plik jest to krok kompilacji i tylko przechowuje dane symboliczne.<br/><br/>Jak zwykłym skompilować procesu, informacje, które nie jest symboliczne, takie jak dodawanie komentarza, zostanie usunięty podczas procesu kompilacji.<br/><br/>Zawsze wtedy, gdy plik .aps synchronizację z pliku .rc, wygenerowania pliku .rc. Na przykład, gdy użytkownik **Zapisz**, Edytor zasobów zastępuje plik .rc i pliku resource.h. Zmiany wprowadzone w zasobach pozostaną dołączone w pliku .rc, ale komentarze zostać utracone po plik .rc jest zastępowany. Aby uzyskać informacje na temat sposobu zachowanie komentarzy, wyświetlić [obejmujące zasoby w czasie kompilowania](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>Zazwyczaj nie powinna zawierać plik .aps w kontroli źródła. |
| .rc | Plik skryptu zasobu, który zawiera skrypt dla zasobów w bieżącym projekcie. Ten plik jest nadpisywany przez plik .aps przy każdym zapisywaniu.<br/><br/>Uwzględnij ten plik w kontroli źródła. |

## <a name="manifest-resources"></a>Zasoby manifestu

W projektach pulpitu C++ manifestu zasoby są plikami XML, które opisują zależności, których używa aplikacja. Na przykład w programie Visual Studio to MFC generowane przez kreatora plik manifestu definiuje, która wersja programu Windows uruchamiający biblioteki dll, aplikacja powinna używać:

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

Dla aplikacji Windows XP lub Windows Vista zasobu manifestu, należy określić najbardziej aktualnej wersji wspólnych formantów Windows dla aplikacji do użycia. W powyższym przykładzie korzysta z wersji `6.0.0.0`, który obsługuje [kontroli Syslink](/windows/desktop/Controls/syslink-overview).

> [!NOTE]
> Może mieć tylko jeden zasób manifestu dla modułu.

Aby wyświetlić wersję i typ informacji zawartych w zasobu manifestu, otwórz plik w podglądzie XML lub Edytor tekstu Visual Studio. Jeśli otwarcie zasobu manifestu z [widok zasobów](../windows/resource-view-window.md), zasób zostanie otwarty w formacie binarnym.

### <a name="to-open-a-manifest-resource"></a>Aby otworzyć zasobu manifestu

1. Otwórz projekt w programie Visual Studio i przejdź do **Eksploratora rozwiązań**.

1. Rozwiń **pliki zasobów** folder, a następnie:

   - Aby otworzyć w edytorze tekstów, kliknij dwukrotnie plik .manifest.

   - Aby otworzyć program w innym edytorze, kliknij prawym przyciskiem myszy plik .manifest, a następnie wybierz **Otwórz za pomocą...** . Określ edytora, aby użyć, a następnie wybierz **Otwórz**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>