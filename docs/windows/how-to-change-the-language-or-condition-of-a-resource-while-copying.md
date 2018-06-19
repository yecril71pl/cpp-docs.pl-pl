---
title: 'Porady: zmiana języka lub warunku zasobu podczas kopiowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.changing
dev_langs:
- C++
helpviewer_keywords:
- Language property
- condition property of resource
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fcddbc0bb5a2afe807cbe8ca7643a831c28ad50f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880140"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying"></a>Porady: zmiana języka lub warunku zasobu podczas kopiowania
Podczas kopiowania w zasobie, można zmienić jej właściwość języka i/lub właściwość condition.  
  
-   Język zasobu identyfikuje właśnie tę, język dla zasobu. Ten element jest używany przez [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) zidentyfikować zasobu, którego szukasz. (Zasobów można jednak różnice dla każdego języka, które nie są powiązane z tekstu, na przykład akceleratorów, które mogą działać tylko na klawiaturę japoński lub mapy bitowej, które będą tylko właściwe dla języka chińskiego zlokalizowane kompilacje itp.)  
  
-   Stan zasobu jest zdefiniowany symbol, który identyfikuje warunku, pod którym ma być używany tej konkretnej kopii zasobu.  
  
 Język i warunku zasobu są wyświetlane w nawiasach po nazwie zasobu w oknie obszaru roboczego. W tym przykładzie zasobów o nazwie IDD_AboutBox używa fiński jako języka i jego stan jest XX33.  
  
```  
IDD_AboutBox (Finnish - XX33)  
```  
  
### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Skopiuj istniejący zasób i zmieniać jego języka lub warunku  
  
1.  Plik .rc lub w [widok zasobów](../windows/resource-view-window.md) okna, kliknij prawym przyciskiem myszy zasób, którego chcesz skopiować.  
  
2.  Wybierz **wstawić kopii** z menu skrótów.  
  
3.  W **wstawić kopii zasobu** okno dialogowe:  
  
    -   Aby uzyskać **języka** pola listy, wybierz język.  
  
    -   W **warunku** wpisz warunek.  
  

  
 Wymagania  
  
 Win32  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: Kopiowanie zasobów](../windows/how-to-copy-resources.md)   
 [Pliki zasobów](../windows/resource-files-visual-studio.md)   
 [Edytory zasobów](../windows/resource-editors.md)