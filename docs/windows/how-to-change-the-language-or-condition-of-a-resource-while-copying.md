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
ms.openlocfilehash: 508655dbfeb2d06d936d2b73d5435cf04c860f4b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598937"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying"></a>Porady: zmiana języka lub warunku zasobu podczas kopiowania

Podczas kopiowania w zasobach, można zmienić jego właściwość języka i/lub właściwości warunku.

- Język zasobu identyfikuje taką, języka zasobu. Jest on używany przez [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) ułatwia zidentyfikowanie zasobów, dla których potrzebujesz. (Zasobów można jednak różnice dla każdego języka, które nie są powiązane z tekstu, na przykład akceleratorów, które może działać wyłącznie względem klawiatury japońskiej lub mapy bitowej, która byłaby tylko odpowiednie dla zlokalizowanego języka chińskiego kompilacje itp.)

- Stan zasobu jest zdefiniowany symbol, który określa warunek, w ramach której ma zostać użyty określonej kopii zasobu.

Język i warunku zasobu są wyświetlane w nawiasach, po nazwie zasobu w okno obszaru roboczego. W tym przykładzie zasobu o nazwie IDD_AboutBox fiński jako używa języka, a jego stan jest XX33.

```cpp
IDD_AboutBox (Finnish - XX33)  
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Aby skopiować istniejący zasób i zmień jego języka lub warunku

1. W pliku .rc, lub w [widok zasobów](../windows/resource-view-window.md) okna, kliknij prawym przyciskiem myszy zasób, którego chcesz skopiować.

2. Wybierz **Wstaw kopiowania** z menu skrótów.

3. W **Wstaw kopię zasobu** okno dialogowe:

   - Aby uzyskać **języka** pola listy, wybierz język.

   - W **warunek** wpisz warunek.

## <a name="requirements"></a>Wymagania

Win32

## <a name="see-also"></a>Zobacz też

[Instrukcje: zasoby dotyczące kopiowania](../windows/how-to-copy-resources.md)  
[Pliki zasobów](../windows/resource-files-visual-studio.md)  
[Edytory zasobów](../windows/resource-editors.md)