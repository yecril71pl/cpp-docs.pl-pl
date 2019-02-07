---
title: Zasoby manifestu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- manifest resources [C++]
- resources [C++], manifest
- resources [C++], opening
ms.assetid: 8615334c-22a0-44c0-93e0-5924528c9917
ms.openlocfilehash: 2d135cb2d512313f107eef7e95ec90d7972b68b4
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850193"
---
# <a name="manifest-resources-c"></a>Zasoby manifestu (C++)

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

Dla aplikacji Windows XP lub Windows Vista zasobu manifestu nie tylko określa, że aplikacja używać najnowszej wersji wspólnych formantów Windows (w wersji 6.0, jak pokazano powyżej), ale obsługuje ona również [kontroli Syslink](/windows/desktop/Controls/syslink-overview).

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*.

Aby wyświetlić wersję i typ informacji zawartych w zasobu manifestu, można otworzyć go w podglądzie XML lub Edytor tekstu Visual Studio. Jeśli otwarcie zasobu manifestu z [widok zasobów](../windows/resource-view-window.md), zasób zostanie otwarty w formacie binarnym. Aby wyświetlić zawartość zasobu manifestu w postaci bardziej widoczne, należy otworzyć zasób z **Eksploratora rozwiązań**.

## <a name="to-open-a-manifest-resource-in-the-text-editor"></a>Aby otworzyć zasobu manifestu w edytorze tekstu

1. Za pomocą projektu Otwórz w programie **Eksploratora rozwiązań**, rozwiń węzeł **pliki zasobów** folderu.

1. Kliknij dwukrotnie plik .manifest.

   Zasobu manifestu zostanie otwarty w **edytora tekstów**.

## <a name="to-open-a-manifest-resource-in-another-editor"></a>Aby otworzyć zasobu manifestu w innym edytorze

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik .manifest i wybierz **Otwórz za pomocą...**  z menu skrótów.

1. W **Otwórz za pomocą** okno dialogowe, określ edytora, o których chcesz użyć, a następnie wybierz pozycję **Otwórz**.

## <a name="limitations"></a>Ograniczenia

Może mieć tylko jeden zasób manifestu dla modułu.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)<br/>
[Praca z plikami zasobów](../windows/working-with-resource-files.md)