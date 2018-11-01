---
title: Zaznaczanie obszaru obrazu (Edytor obrazów dla ikon)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 5e2522d23b30a91639e887a8761871e3df8139f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565116"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Zaznaczanie obszaru obrazu (Edytor obrazów dla ikon)

Narzędzia wyboru służy do definiowania obszar obrazu, który ma być wycinanie, kopiowanie, wyczyść, zmienić rozmiar, Odwróć lub przenoszenie. Za pomocą **prostokąta zaznaczenia** narzędzie można definiować i wybierz prostokątny obszar obrazu. Za pomocą **kształt** narzędzia można narysować freehand konspektu obszaru, który chcesz wybrać opcjami wycinania, kopiowania lub inna operacja.

> [!NOTE]
> Zobacz **prostokąta zaznaczenia** i **kształt** na schemacie narzędzia [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md) lub wyświetlanie etykietek narzędzi, skojarzone z każdego przycisku w **Edytora obrazów** paska narzędzi.

Można również utworzyć niestandardowy obiekt brush z zaznaczenia. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-select-an-area-of-an-image"></a>Aby wybrać obszar obrazu

1. Na **edytora obrazów** narzędzi (lub z **obrazu** menu **narzędzia** polecenie), kliknij pozycję Narzędzia zaznaczania ma.

2. Przesuń punkt wstawiania do jednego rogu obszaru obrazu, który ma zostać wybrana. Na ekranie są wyświetlane, gdy punkt wstawiania znajduje się na obrazie.

3. Przeciągnij kursor przeciwległego rogu obszaru, który ma zostać wybrana. Prostokąt pokazuje, które piksele zostanie wybrany. Wszystkie piksele w obrębie prostokąta, łącznie z tymi w ramach prostokąt, są uwzględnione w zaznaczeniu.

4. Zwolnij przycisk myszy. Obramowanie wyboru otacza zaznaczonego obszaru.

### <a name="to-select-an-entire-image"></a>Aby wybrać całego obrazu

1. Kliknij obraz, poza bieżącym zaznaczeniu. Krawędź zaznaczenia zmienia fokus i obejmuje cały obraz jeszcze raz.

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)