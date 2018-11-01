---
title: 'Porady: zmiana języka lub warunku zasobu podczas kopiowania (C++)'
ms.date: 11/04/2016
f1_keywords:
- vc.resvw.resource.changing
helpviewer_keywords:
- Language property [C++]
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
ms.openlocfilehash: 42d8fb36dcbd243b0a99f2dbc597bdf352f47266
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642523"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying-c"></a>Porady: zmiana języka lub warunku zasobu podczas kopiowania (C++)

Podczas kopiowania w zasobach, można zmienić jego właściwość języka i/lub właściwości warunku.

- Język zasobu identyfikuje taką, języka zasobu. Jest on używany przez [FindResource](/windows/desktop/api/winbase/nf-winbase-findresourcea) ułatwia zidentyfikowanie zasobów, dla których potrzebujesz. (Zasobów można jednak różnice dla każdego języka, które nie są powiązane z tekstu, na przykład akceleratorów, które może działać wyłącznie względem klawiatury japońskiej lub mapy bitowej, która byłaby tylko odpowiednie dla zlokalizowanego języka chińskiego kompilacje itp.)

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

[Instrukcje: zasoby dotyczące kopiowania](../windows/how-to-copy-resources.md)<br/>
[Pliki zasobów](../windows/resource-files-visual-studio.md)<br/>
[Edytory zasobów](../windows/resource-editors.md)