---
title: Obraz Menu (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- Image menu
ms.assetid: ac2b4d53-1919-4fd1-a0af-d3c085c45af2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f8a1e5acdd2f17101f61866e050e7a28f80ea837
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019790"
---
# <a name="image-menu-image-editor-for-icons"></a>Menu obrazu (Edytor obrazów dla ikon)
**Obraz** menu, która jest wyświetlana tylko wtedy, gdy **obraz** edytora jest aktywny, zawiera polecenia służące do edycji obrazów, zarządzanie palety kolorów i ustawienie **edytora obrazów** okna Opcje. Ponadto polecenia narzędzia obrazach urządzeń są dostępne podczas pracy z ikony i kursory.  
  
 **Odwróć kolory**  
 Odwraca kolory. Aby uzyskać więcej informacji, zobacz [odwracanie kolorów w wyborze](../windows/inverting-the-colors-in-a-selection-image-editor-for-icons.md).  
  
 **Przerzuć w poziomie**  
 Przerzuca obraz lub zaznaczenie w poziomie. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Przerzuć w pionie**  
 Przerzuca obraz lub zaznaczenie w pionie. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Obrót o 90 stopni**  
 Obraca obraz lub zaznaczenie o 90 stopni. Aby uzyskać więcej informacji, zobacz [Przerzucanie obrazu](../windows/flipping-an-image-image-editor-for-icons.md).  
  
 **Pokaż okno kolorów**  
 Otwiera [okno kolorów](../windows/colors-window-image-editor-for-icons.md), w którym możesz wybrać kolory używane dla obrazu. Aby uzyskać więcej informacji, zobacz [Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md).  
  
 **Użyj zaznaczenia jako pędzla**  
 Umożliwia tworzenie pędzla niestandardowego na podstawie część obrazu. Wybór staje się pędzla niestandardowego, który rozdziela kolorów w wyborze między obrazu. Kopiuje zaznaczenie są pozostawiane w ścieżce przeciągania. Przeciągniesz wolniej, większej liczby kopii zostały wprowadzone. Aby uzyskać więcej informacji, zobacz [Tworzenie pędzla niestandardowego](../windows/creating-a-custom-brush-image-editor-for-icons.md).  
  
 **Kopiuj i wybór konspektu**  
 Tworzy kopię bieżącego zaznaczenia i zakreśla ją. Jeśli kolor tła znajduje się w bieżącym zaznaczeniu, będzie on wykluczony, jeśli masz [przezroczyste](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) wybrane.  
  
 **Dostosuj kolory**  
 Otwiera [selektor kolorów niestandardowych](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md), co pozwala dostosować kolory używane dla obrazu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie lub zmiana kolorów](../windows/customizing-or-changing-colors-image-editor-for-icons.md).  
  
 **Załaduj paletę**  
 Otwiera [Załaduj paletę kolorów, okno dialogowe](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), co umożliwia ładowanie kolorów palety wcześniej zapisane w pliku .pal.  
  
 **Zapisz paletę**  
 Zapisuje w pliku .pal kolorów palety.  
  
 **Rysuj nieprzezroczyste**  
 Po wybraniu sprawia, że bieżące zaznaczenie nieprzezroczystości. Po wyczyszczeniu, sprawia, że bieżące zaznaczenie przezroczyste. Aby uzyskać więcej informacji, zobacz [wybierania nieprzezroczyste lub przezroczyste tło](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 **Edytor paska narzędzi**  
 Otwiera [okno dialogowe Nowy zasób paska narzędzi](../windows/new-toolbar-resource-dialog-box.md).  
  
 **Ustawienia siatki**  
 Otwiera [okno dialogowe Ustawienia siatki](../windows/grid-settings-dialog-box-image-editor-for-icons.md) w którym można określić siatki dla obrazu.  
  
 **Nowy typ obrazu**  
 Otwiera [New \<urządzenia > okno dialogowe typu obrazu](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md). Zasób pojedyncza ikona może zawierać kilka obrazów o różnych rozmiarach; Windows użyć rozmiaru odpowiednią ikonę w zależności od tego, jak będzie mają być wyświetlane. Nowy typ urządzenia nie powoduje modyfikacji rozmiar ikony, ale raczej tworzy nowy obraz w ramach ikony. Dotyczy tylko ikony i kursory.  
  
 **Bieżący typ obrazu ikony/kursora**  
 Spowoduje otwarcie podmenu zawierającego pierwszy dostępnych kursorem lub ikonę obrazów (dziewięć pierwszy). Ostatnie polecenie, w podmenu, **więcej...** , otwiera [Otwórz \<urządzenia > okno dialogowe obrazu](../windows/open-device-image-dialog-box-image-editor-for-icons.md).  
  
 **Usuń typ obrazu**  
 Usuwa obraz wybranego urządzenia.  
  
 **Narzędzia**  
 Uruchamia podmenu, który zawiera wszystkie dostępne narzędzia [paska narzędzi edytora obrazów](../windows/toolbar-image-editor-for-icons.md).  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)