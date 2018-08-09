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
ms.openlocfilehash: b990046e4f43e70218fc1a7f6eb885638c2051bf
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40015946"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Zapisywanie i ładowanie różnych palet kolorów (Edytor obrazów dla ikon)
Można zapisać i załadować **kolory** palety, który zawiera [dostosować kolory](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Domyślnie **kolory** palety ostatnio używane jest automatycznie ładowany podczas uruchamiania programu Visual Studio.)  
  
> [!TIP]
>  Ponieważ **obraz** edytor nie ma żadnych środków, aby przywrócić domyślne **kolory** palety, należy zapisać domyślne **kolory** palety w obszarze nazwy, takie jak  *Standard.PAL* lub *default.pal* tak, aby można je łatwo przywrócić ustawienia domyślne.  
  
### <a name="to-save-a-custom-colors-palette"></a>Aby zapisać palety kolorów niestandardowych  
  
1.  Z **obraz** menu, wybierz **Zapisz paletę**.  
  
2.  Przejdź do katalogu, w którym chcesz zapisać palety, a następnie wpisz nazwę palety.  
  
3.  Kliknij przycisk **Zapisz**.  
  
### <a name="to-load-a-custom-colors-palette"></a>Aby załadować palety kolorów niestandardowych  
  
1.  Z **obraz** menu, wybierz **Załaduj paletę**.  
  
2.  W [Załaduj paletę kolorów, okno dialogowe](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), przejdź do katalogu poprawny i wybierz paletę chcesz załadować. **Kolor** palet są zapisywane wraz z rozszerzeniem pliku .pal.  
  
## <a name="requirements"></a>Wymagania  
 Brak  
  
## <a name="see-also"></a>Zobacz też  
 [Klawisze skrótów](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Praca z kolorem](../windows/working-with-color-image-editor-for-icons.md)