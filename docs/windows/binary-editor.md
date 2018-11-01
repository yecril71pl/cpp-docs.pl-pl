---
title: Edytor plików binarnych (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.binary.F1
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 1b5e1c16ff63c55617ee9b2bbcb47a7201635789
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451704"
---
# <a name="binary-editor-c"></a>Edytor plików binarnych (C++)

> [!WARNING]
> **Edytor plików binarnych** nie jest dostępny w wersji Express.

W edytorze binarnym służy do edytowania dowolnego zasobu w poziomie binarnym w formacie szesnastkowym lub w formacie ASCII. Można również użyć [znaleźć polecenia](/visualstudio/ide/reference/find-command) do wyszukiwania ciągów znaków ASCII lub bajty szesnastkowe. Należy używać **binarne** edytora tylko wtedy, gdy należy wyświetlić lub wprowadzić drobne zmiany zasoby niestandardowe lub typy zasobów, które nie są obsługiwane przez środowisko Visual Studio.

Aby otworzyć **Edytor plików binarnych**, należy najpierw wybrać **pliku** > **nowy** > **pliku** wybierz z menu głównego plik który chcesz edytować, a następnie kliknij strzałkę listy obok **Otwórz** przycisk, a następnie wybierz **Otwórz za pomocą** > **Edytor plików binarnych**.

> [!CAUTION]
> Edytowanie zasobów, takich jak okna dialogowe, obrazów lub menu w edytorze binarnym jest niebezpieczne. Niepoprawne edytowanie może spowodować uszkodzenie zasobów, dzięki czemu można odczytać w edytorze natywnych.

> [!TIP]
> Podczas korzystania z **binarne** edytora w wielu przypadkach możesz kliknąć prawym przyciskiem myszy, aby wyświetlić menu skrótów poleceń specyficznych dla zasobów. Dostępne polecenia zależą od tego, co kursor wskazuje. Na przykład jeśli klikniesz podczas wskazujący **binarne** Edytor przy użyciu wybranej wartości szesnastkowych, pokazuje, w menu skrótów **Wytnij**, **kopiowania**, i **wklejania**  poleceń.

Za pomocą **binarne** edytora, możesz:

- [Otwórz zasób do edycji plików binarnych](../windows/opening-a-resource-for-binary-editing.md)

- [Edytowanie danych binarnych](../windows/editing-binary-data.md)

- [Znajdowanie danych binarnych](../windows/finding-binary-data.md)

- [Utwórz nowy zasób niestandardowy lub danych](../windows/creating-a-new-custom-or-data-resource.md)

## <a name="managed-resources"></a>Zarządzane zasoby

Możesz użyć [edytora obrazów](../windows/image-editor-for-icons.md) i **binarne** edytora, aby pracować z plikami zasobów w zarządzanych projektów. Wszelkie zarządzane zasoby, które chcesz edytować, muszą być powiązanymi zasobami. Edytory zasobów programu Visual Studio nie obsługują edycji zasobów osadzonych.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Edytory zasobów](../windows/resource-editors.md)