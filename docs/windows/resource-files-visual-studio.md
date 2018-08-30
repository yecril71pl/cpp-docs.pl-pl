---
title: Pliki zasobów (Visual Studio) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio]
- .rc files
- resource files
- resource script files
- resource script files, Win-32 based applications
- resource script files, files updated when editing resources
- resources [Visual Studio], types of resource files
- rct files
- resources [C++]
- rc files
- resource files, types of
- .rct files
- resource script files, unsupported types
ms.assetid: 4d2b6fcc-07cf-4289-be87-83a60f69533c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99cf5f3c1eb0a81a636407a722149d6cee1bee64
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43220689"
---
# <a name="resource-files-visual-studio"></a>Pliki zasobów (Visual Studio)

> [!NOTE]
> W tym materiale dotyczy aplikacje pulpitu Windows. Aby uzyskać informacje dotyczące zasobów w aplikacji platformy uniwersalnej Windows, zobacz [Definiowanie zasobów aplikacji](https://msdn.microsoft.com/476ea844-632c-4467-9ce3-966be1350dd4).
>
> Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).
>
> Ponieważ projekty w językach programowania .NET należy używać plików skryptu zasobu, należy otworzyć swoich zasobów przed **Eksploratora rozwiązań**. Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i [edytorze binarnym](binary-editor.md) do pracy z plikami zasobów w projektach zarządzanych. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Termin "pliku zasobów" może odwoływać się do wielu typów plików, w tym:

- Plik skryptu (.rc) zasobów programu.

- Plik szablonu (.rct) zasobów.

- Pojedynczy zasób istniejące jako autonomiczny plik, takiego jak plik mapy bitowej, ikona lub kursor jest to określane w pliku .rc.

- Plik nagłówka, generowane przez środowisko programistyczne, na przykład Resource.h, który jest określany w pliku .rc.

Zasoby można również znaleźć w [innych typów plików](../windows/editable-file-types-for-resources.md) takich jak pliki .exe i .dll, .res. Możesz pracować z zasobami i plikami zasobów z w obrębie projektu i z tymi, które nie są częścią bieżącego projektu. Może również współdziałać z plikami zasobów, które nie zostały utworzone w środowisku projektowym programu Visual Studio. Możesz na przykład:

- Praca z plikami zasobów zagnieżdżone i dołączane warunkowo.

- Aktualizowanie istniejących zasobów lub konwersji do formatu Visual C++.

- Importowanie lub eksportowanie zasobów graficznych do lub z bieżącego pliku zasobów.

- Obejmują udostępnione lub tylko do odczytu identyfikatorów (symbolom), których nie można zmodyfikować przez środowisko programistyczne.

- Obejmują zasobów w pliku wykonywalnym (.exe), które nie wymagają do edycji (lub nie chcesz edytować) w bieżącym projekcie, takich jak zasoby, które są wspólne dla kilku projektów.

- Obejmują typy zasobów, które nie są obsługiwane przez środowisko programistyczne.

W tej sekcji omówiono:

- [Tworzenie nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md)

- [Tworzenie nowego zasobu](../windows/how-to-create-a-resource.md)

- [Przeglądanie zasobów w pliku skryptu zasobu](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)

- [Otwieranie pliku skryptu zasobu w formacie tekstowym](../windows/how-to-open-a-resource-script-file-in-text-format.md)

- [Czas kompilacji w tym zasobów w](../windows/how-to-include-resources-at-compile-time.md)

- [Kopiowanie zasobów](../windows/how-to-copy-resources.md)

- [Korzystanie z szablonów zasobów (.rct)](../windows/how-to-use-resource-templates.md)

- [Importowanie i eksportowanie zasobów](../windows/how-to-import-and-export-resources.md)

- [Edytowalne typy plików dla zasobów](../windows/editable-file-types-for-resources.md)

- [Pliki, których dotyczy edytowanie zasobów](../windows/files-affected-by-resource-editing.md)

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)  
[Praca z plikami zasobów](../windows/working-with-resource-files.md)  
[Menu i inne zasoby](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)