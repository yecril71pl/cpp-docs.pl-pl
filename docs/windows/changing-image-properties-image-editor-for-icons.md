---
title: Zmiana właściwości obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f3c03cfa1d1d9a30cf6639b04937bacff473d7c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42604636"
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Zmiana właściwości obrazu (Edytor obrazów dla ikon)

Można ustawić lub zmodyfikować właściwości obrazu, użyj [okno właściwości](/visualstudio/ide/reference/properties-window).

### <a name="to-change-an-images-properties"></a>Aby zmienić właściwości obrazu

1. Otwórz obraz w **obraz** edytora.

2. W **właściwości** okna, zmiana dowolnych lub wszystkich właściwości dla obrazu.

   |Właściwość|Opis|
   |--------------|-----------------|
   |**Kolory**|Określa schemat kolorów dla obrazu. Wybierz **monochromatyczny**, **16**, lub **256**, lub **True Color**. Jeśli użytkownik narysuje już obraz z paletę 16 kolorów, wybierając **monochromatyczny** powoduje, że podstawienia białe kolorów na obrazie. Kontrast nie jest zawsze utrzymywane: na przykład obszarami pokrewnymi czerwonego i zielonego są zarówno konwertowane na czarny.|
   |**Nazwa pliku**|Określa nazwę pliku obrazu. Domyślnie program Visual Studio przypisuje podstawowej nazwy pliku tworzone przez usunięcie pierwsze cztery znaki ("IDB_") z domyślnego identyfikatora zasobu (IDB_BITMAP1) i dodawanie odpowiedniego rozszerzenia. Nazwa pliku obrazu, w tym przykładzie byłaby `BITMAP1.bmp`. Można zmienić jego nazwę `MYBITMAP1.bmp`.|
   |**Wysokość**|Określa wysokość obrazu (w pikselach). Wartość domyślna to 48. Obraz zostanie przycięty lub puste miejsce jest dodawana poniżej istniejącego obrazu.|
   |**ID**|Ustawia identyfikator zasobu. Obraz programu Microsoft Visual Studio domyślnie przypisuje następny dostępny identyfikator w serii: IDB_BITMAP1, IDB_BITMAP2, itd. Podobne nazwy są używane do ikony i kursory.|
   |**Paleta**|Zmiany kolorów właściwości. Kliknij dwukrotnie, aby wybrać kolor i wyświetlić [okno dialogowe selektora kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednich polach.|
   |**SaveCompressed**|Wskazuje, czy obraz jest w formacie skompresowanym. Ta właściwość jest tylko do odczytu. Visual Studio pozwala zapisać obrazy w formacie skompresowany, więc wszystkie obrazy utworzone w programie Visual Studio, ta właściwość będzie miał **False**. Jeśli otworzysz skompresowanego obrazu (utworzonym w innym programie) w programie Visual Studio, ta właściwość będzie miał **True**. Jeśli zapiszesz skompresowanego obrazu za pomocą programu Visual Studio, będzie ona bez kompresji i ta właściwość zostanie przywrócona do **False**.|
   |**Szerokość**|Ustawia szerokość obrazu (w pikselach). Wartość domyślna dla map bitowych to 48. Obraz zostanie przycięty lub puste miejsce zostanie dodany do istniejącego obrazu po prawej stronie.|

Aby uzyskać informacje na temat dodawania zasobów do projektów zarządzanych, zobacz [zasoby w aplikacjach pulpitu](/dotnet/framework/resources/index) w *przewodniku dewelopera .NET Framework*. Aby uzyskać informacji na temat ręcznego dodawania plików zasobów do projektów zarządzanych, uzyskiwania dostępu do zasobów, wyświetlania statycznych zasobów i przypisywania ciągów zasobów do właściwości, zobacz [Creating Resource Files dla aplikacji klasycznych](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Aby uzyskać informacji na temat globalizacja i lokalizacja zasobów w aplikacjach zarządzanych, zobacz [Globalizing i lokalizowanie aplikacji programu .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Wymagania

Brak

## <a name="see-also"></a>Zobacz też

[Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)  
[Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)