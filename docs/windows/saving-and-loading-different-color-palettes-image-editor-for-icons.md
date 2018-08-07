---
title: Zapisywanie i ładowanie różnych kolorów palety (edytor obrazów dla ikon) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 14cad19c53e8cd741bf16bab49420169e93f6af6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606975"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Zapisywanie i ładowanie różnych palet kolorów (Edytor obrazów dla ikon)
Można zapisać i załadować paleta kolorów, która zawiera [dostosować kolory](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Domyślnie paleta kolorów, ostatnio używane jest automatycznie ładowany podczas uruchamiania programu Visual Studio.)  
  
> [!TIP]
>  Ponieważ edytora obrazów nie oznacza, że można przywrócić domyślną paletę kolorów, należy zapisać paleta kolorów domyślne w obszarze nazwy, takie jak standard.pal lub default.pal tak, aby można je łatwo przywrócić ustawienia domyślne.  
  
### <a name="to-save-a-custom-colors-palette"></a>Aby zapisać palety kolorów niestandardowych  
  
1.  Z **obraz** menu, wybierz **Zapisz paletę**.  
  
2.  Przejdź do katalogu, w którym chcesz zapisać palety, a następnie wpisz nazwę palety.  
  
3.  Kliknij przycisk **Zapisz**.  
  
### <a name="to-load-a-custom-colors-palette"></a>Aby załadować palety kolorów niestandardowych  
  
1.  Z **obraz** menu, wybierz **Załaduj paletę**.  
  
2.  W [Załaduj paletę kolorów, okno dialogowe](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), przejdź do katalogu poprawny i wybierz paletę chcesz załadować. Palety kolorów są zapisywane z rozszerzeniem pliku .pal.  
  
## <a name="requirements"></a>Wymagania  
  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)