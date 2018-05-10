---
title: Tworzenie pędzla niestandardowego (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a879850c00957568065150b6c6fc1c801c049fa2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>Tworzenie pędzla niestandardowego (Edytor obrazów dla ikon)
Pędzla niestandardowego jest prostokątny część obrazu, który Podnieś i użyj podobny do pędzli gotowe edytor obrazów. Wszystkie operacje, które można wykonywać na wybranych, można wykonywać na również pędzla niestandardowego.  
  
### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Aby utworzyć pędzla niestandardowego z części obrazu  
  
1.  [Wybierz część obrazu](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) , który ma być używany dla pędzla.  
  
2.  Zawierający **SHIFT** klucza w dół, kliknij w zaznaczeniu i przeciągnij go przez obraz.  
  
     \- lub -  
  
3.  Z **obrazu** menu, wybierz **Użyj wyboru jako pędzel**.  
  
     Wybór staje się pędzla niestandardowego dystrybuująca kolorów w wyborze w obrazie. Kopiuje zaznaczenie pozostają na ścieżce przeciągania. Przeciągnij wolniej, większej liczby kopii zostaną zastosowane.  
  
     **Uwaga** kliknięcie przycisku **użyć opcji pędzla** bez polega na wybraniu część obrazu użyje całego obrazu jako pędzla. Wynik przy użyciu pędzla niestandardowego również zależy od tego, czy wybrano [tła nieprzezroczyste lub przezroczysty](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 Pikseli pędzla niestandardowego zgodne bieżący kolor tła są zwykle niewidoczne: ich nie malowanie istniejącego obrazu. Aby zmienić to zachowanie, dzięki czemu pikseli kolor tła malowanie istniejącego obrazu.  
  
 Niestandardowe pędzla sygnatury lub wzornik służy do tworzenia szerokiej gamy efekty specjalne.  
  
#### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Rysowanie kształtów pędzla niestandardowego w kolor tła  
  
1.  [Wybierz tło przezroczystości](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
2.  [Kolor tła](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) kolor, w którym chcesz narysować.  
  
3.  Ustaw pędzla niestandardowego gdzie do rysowania.  
  
4.  Kliknij prawym przyciskiem myszy. Wszystkie regiony nieprzezroczyste pędzla niestandardowego są rysowane w kolor tła.  
  
#### <a name="to-double-or-halve-the-custom-brush-size"></a>Kliknij dwukrotnie lub połowę rozmiar pędzla niestandardowego  
  
1.  Naciśnij klawisz **znak PLUS** (**+**) klucz podwojenia pędzla, lub **znak MINUS** (**-**) kluczem o połowę go .  
  
#### <a name="to-cancel-the-custom-brush"></a>Aby anulować pędzla niestandardowego  
  
1.  Naciśnij klawisz **ESC** lub wybierz inne narzędzie do rysowania.  
  
 Aby uzyskać informacje o dodawaniu zasobów do projektów zarządzanych, zobacz [zasobów w aplikacjach pulpitu](/dotnet/framework/resources/index) w *Przewodnik programistów platformy .NET Framework.* Aby uzyskać informacje na ręczne dodanie do projektów zarządzanych plików zasobów, uzyskiwanie dostępu do zasobów, wyświetlanie zasoby statyczne i przypisanie do właściwości ciągów zasobów, zobacz [tworzenie plików zasobów dla aplikacji pulpitu](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informacje dotyczące globalizacji i lokalizacji zasobów w zarządzanych aplikacjach, zobacz [Globalizing i lokalizacja aplikacji .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Edytowanie zasobów graficznych](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Edytor obrazów dla ikon](../windows/image-editor-for-icons.md)

