---
title: Wyświetlanie podglądu zasobów (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
helpviewer_keywords:
- resources [C++], viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
ms.openlocfilehash: 79756bd71dfc731b78b21bd4df311e4848beb899
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50589556"
---
# <a name="previewing-resources"></a>Wyświetlanie podglądu zasobów

Wyświetlanie podglądu zasobów służy do wyświetlania zasobów graficznych bez ich otwierania. Podgląd jest również przydatne dla plików wykonywalnych, po ich skompilowany, ponieważ zmiany numery identyfikatorów zasobów. Ponieważ te identyfikatory numeryczne często nie zapewniają wystarczających informacji, wyświetlanie podglądu zasobów pomaga szybko określić ich.

Możesz wyświetlić podgląd wizualnym układem następujących zasobów:

- Mapy bitowej

- Okno dialogowe

- Ikona

- Menu

- Kursor

- Pasek narzędzi

Funkcja wyświetlania podglądu nie ma zastosowania do zasobów akceleratora, Manifest, Tabela ciągów i informacje o wersji.

### <a name="to-preview-resources"></a>Aby wyświetlić podgląd zasobów

1. W [widok zasobów](../windows/resource-view-window.md) lub okno dokumentu, wybierz zasób, na przykład **IDD_ABOUTBOX**.

   > [!NOTE]
   > Jeśli projekt nie zawiera jeszcze pliku .rc, zobacz [tworzenia nowego pliku skryptu zasobów](../windows/how-to-create-a-resource-script-file.md).

2. W [okno właściwości](/visualstudio/ide/reference/properties-window), kliknij przycisk **stron właściwości** przycisku.

   \- lub —

3. Na **widoku** menu, kliknij przycisk **stron właściwości**.

   **Strona właściwości** zasobu zostanie otwarty w wersji zapoznawczej tego zasobu. Następnie można użyć **się** i **dół** klawiszy strzałek, aby przejść w drzewie w kontrolce **widok zasobów** lub okno dokumentu. **Strona właściwości** będzie pozostają otwarte i Pokaż dowolnego zasobu, który ma fokus i jest w stanie można wyświetlić podglądu.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: otwieranie pliku skryptu zasobu spoza projektu (autonomicznego)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)