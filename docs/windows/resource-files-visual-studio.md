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
ms.openlocfilehash: 463c27959b049436e29f872c966bc276c6ef5f2d
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507022"
---
# <a name="resource-files-c"></a>Pliki zasobów (C++)

> [!NOTE]
> Ponieważ projekty w językach programowania .NET nie używają plików skryptów zasobów, należy otworzyć zasoby z **Eksplorator rozwiązań**. Użyj [edytora obrazów](../windows/image-editor-for-icons.md) i [edytora binarnego](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych.
>
> Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Termin *plik zasobów* może odwoływać się do wielu typów plików, takich jak:

- Plik skryptu zasobu (. RC) programu.

- Plik szablonu zasobu (. rct).

- Pojedynczy zasób istniejący jako plik autonomiczny. Ten typ zawiera mapę bitową, ikonę lub plik kursora, do którego odwołuje się plik. rc.

- Plik nagłówka generowany przez środowisko deweloperskie. Ten typ obejmuje `Resource.h` , który jest określany na podstawie pliku. rc.

Zasoby znajdujące się w innych typach plików, takich jak pliki exe, DLL i. res, są określane jako *zasoby*.

Z poziomu projektu można korzystać z *plików zasobów* i *zasobów* . Można również korzystać z tych, które nie są częścią bieżącego projektu lub zostały utworzone poza środowiskiem programistycznym programu Visual Studio. Możesz na przykład:

- Pracuj z zagnieżdżonymi i warunkowo plikami zasobów.

- Zaktualizuj istniejące zasoby lub Przekonwertuj je na Visual C++.

- Importuj lub Eksportuj zasoby graficzne do lub z bieżącego pliku zasobów.

- Uwzględnij identyfikatory udostępnione lub tylko do odczytu (symbole), które nie mogą być modyfikowane przez środowisko programistyczne.

- Uwzględnij zasoby w pliku wykonywalnym (exe), które nie wymagają edytowania (lub nie powinny być edytowane), takie jak zasoby udostępnione między kilkoma projektami.

- Uwzględnij typy zasobów nieobsługiwane przez środowisko programistyczne.

Aby uzyskać więcej informacji o zasobach, zobacz How to [Create Resources](../windows/how-to-create-a-resource-script-file.md), [Manage Resources](../windows/how-to-copy-resources.md)i include Resources [w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md).

## <a name="editable-resources"></a>Zasoby edytowalne

Aby edytować zawarte w nich zasoby, można otworzyć następujące typy plików:

| Nazwa pliku | Opis |
|---|---|
| . RC | Pliki skryptów zasobów |
| . RCT | Pliki szablonów zasobów |
| . res | Pliki zasobów |
| .resx | Zarządzane pliki zasobów |
| .exe | Pliki wykonywalne |
| .dll | Pliki bibliotek dołączanych dynamicznie |
| . bmp,. ico,. DIB,. CUR | Pliki map bitowych, ikon, pasków narzędzi i kursorów |

Podczas edytowania zasobów środowisko programu Visual Studio współpracuje z programem i ma wpływ na następujące pliki:

| Nazwa pliku | Opis |
|---|---|
| Resource.h | Plik nagłówkowy wygenerowany przez środowisko programistyczne, które zawiera definicje symboli.<br/><br/>Uwzględnij ten plik w kontroli źródła. |
| Filename. APS | Wersja binarna bieżącego pliku skryptu zasobów używanego do szybkiego ładowania.<br /><br /> Edytory zasobów nie odczytują bezpośrednio plików. RC lub Resource. h. Kompilator zasobów kompiluje je do plików APS, które są używane przez edytory zasobów. Ten plik jest krokiem kompilacji i przechowuje tylko dane symboliczne.<br/><br/>Podobnie jak w przypadku normalnego procesu kompilowania, informacje, które nie są symboliczne, takie jak komentowanie, są odrzucane podczas procesu kompilacji.<br/><br/>Za każdym razem, gdy plik APS nie jest zsynchronizowany z plikiem. RC, plik. RC zostanie wygenerowany ponownie. Na przykład podczas **zapisywania**Edytor zasobów zastępuje plik. RC i plik Resource. h. Wszelkie zmiany zasobów pozostają zawarte w pliku. RC, ale komentarze są zawsze tracone po nadpisaniu pliku. rc. Aby uzyskać informacje na temat sposobu zachowywania komentarzy, zobacz temat [uwzględnianie zasobów w czasie kompilacji](../windows/how-to-include-resources-at-compile-time.md).<br/><br/>Zazwyczaj nie należy umieszczać pliku APS w kontroli źródła. |
| . RC | Plik skryptu zasobu, który zawiera skrypt dla zasobów w bieżącym projekcie. Ten plik jest zastępowany przez plik APS przy każdym zapisywaniu.<br/><br/>Uwzględnij ten plik w kontroli źródła. |

## <a name="manifest-resources"></a>Zasoby manifestu

W projektach klasycznych w języku C++ zasoby manifestu są plikami XML, które opisują zależności używane przez aplikację. Na przykład w programie Visual Studio ten plik manifestu generowany przez kreatora MFC definiuje, która wersja bibliotek DLL wspólnych systemu Windows ma być używana przez aplikację:

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

W przypadku aplikacji systemu Windows XP lub Windows Vista zasób manifestu powinien określać najbardziej aktualną wersję formantów wspólnych systemu Windows, które mają być używane przez aplikację. W powyższym przykładzie używa się wersji `6.0.0.0` , która obsługuje [formant Syslink](/windows/win32/Controls/syslink-overview).

> [!NOTE]
> Dla każdego modułu można mieć tylko jeden zasób manifestu.

Aby wyświetlić informacje o wersji i typie zawarte w zasobie manifestu, Otwórz plik w przeglądarce XML lub edytorze tekstu programu Visual Studio. Jeśli otworzysz zasób manifestu z [Widok zasobów](./how-to-create-a-resource-script-file.md), zasób zostanie otwarty w formacie binarnym.

### <a name="to-open-a-manifest-resource"></a>Aby otworzyć zasób manifestu

1. Otwórz projekt w programie Visual Studio i przejdź do **Eksplorator rozwiązań**.

1. Rozwiń folder **pliki zasobów** , a następnie:

   - Aby otworzyć program w edytorze tekstów, kliknij dwukrotnie plik *. manifest* .

   - Aby otworzyć w innym edytorze, kliknij prawym przyciskiem myszy plik *. manifest* i wybierz polecenie **Otwórz za pomocą**. Określ Edytor, który ma być używany, a następnie wybierz pozycję **Otwórz**.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Praca z plikami zasobów](../windows/working-with-resource-files.md)<br/>
[Identyfikatory zasobów (symbole)](../windows/symbols-resource-identifiers.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)<br/>
