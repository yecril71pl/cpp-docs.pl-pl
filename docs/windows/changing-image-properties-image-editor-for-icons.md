---
title: "Zmiana właściwości obrazu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- images [C++], properties
- Image editor [C++], Properties window
- Image editor [C++], image properties
- Properties window, image editor
ms.assetid: f6172bf1-08c4-4dfd-b542-dd8749e83fe6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96122b2bdc6419b41cd0e00cb544955d8d7c8463
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="changing-image-properties-image-editor-for-icons"></a>Zmiana właściwości obrazu (Edytor obrazów dla ikon)
Można ustawić lub zmodyfikować właściwości obrazu za pomocą [okna właściwości](/visualstudio/ide/reference/properties-window).  
  
### <a name="to-change-an-images-properties"></a>Aby zmienić właściwości obrazu  
  
1.  Otwórz obraz w **obrazu** edytora.  
  
2.  W **właściwości** okna, zmienianie lub wszystkie właściwości obrazu.  
  
    |Właściwość|Opis|  
    |--------------|-----------------|  
    |**Kolory**|Określa schemat kolorów obrazu. Wybierz kolor monochromatyczny, 16, lub 256 lub wartość True. Gdy ma już rysowane obraz z 16 kolorów palety, zaznaczenie w skali odcieni szarości powoduje, że podstawień białe kolorów w obrazie. Kontrast nie jest zachowywany zawsze: na przykład przylegające obszary czerwony i zielony są oba konwertowane na kolor czarny.|  
    |**Nazwa pliku**|Określa nazwę pliku obrazu. Domyślnie program Visual Studio przypisuje podstawowej nazwy pliku tworzone przez usunięcie pierwsze cztery znaki ("IDB_") z domyślny identyfikator zasobów (IDB_BITMAP1) i dodawanie odpowiedniego rozszerzenia. Nazwa pliku obrazu w tym przykładzie byłaby BITMAP1.bmp. Można ją zmienić MYBITMAP1.bmp.|  
    |**Wysokość**|Określa wysokość obrazu (w pikselach). Wartość domyślna to 48. Obraz jest przycięty lub spacja jest dodawana poniżej istniejącego obrazu.|  
    |**IDENTYFIKATOR**|Określa identyfikator zasobu. Obraz programu Microsoft Visual Studio, domyślnie przypisuje następny identyfikator dostępne w serii: IDB_BITMAP1, IDB_BITMAP2, itd. Podobne nazwy są używane dla ikony i kursory.|  
    |**Palety**|Zmiany kolorów właściwości. Kliknij dwukrotnie, aby wybrać kolor i wyświetlić [wybór koloru niestandardowego — okno dialogowe](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Zdefiniuj kolor, wpisując wartości RGB lub HSL w odpowiednich polach.|  
    |**SaveCompressed**|Wskazuje, czy obraz jest w formacie skompresowanym. Ta właściwość jest tylko do odczytu. Visual Studio nie pozwala na zapisywanie obrazów w formacie skompresowanym tak na wszystkie obrazy utworzone w programie Visual Studio, ta właściwość będzie **False**. Jeśli w programie Visual Studio, możesz otworzyć skompresowanego obrazu (utworzony przez inny program), ta właściwość będzie **True**. Jeśli zapiszesz skompresowanego obrazu przy użyciu programu Visual Studio będzie nieskompresowanych i ta właściwość zostanie przywrócona do **False**.|  
    |**Szerokość**|Ustawia szerokość obrazu (w pikselach). Wartość domyślna dla map bitowych to 48. Obraz jest przycięty lub puste miejsce jest dodawana do istniejącego obrazu z prawej strony.|  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

