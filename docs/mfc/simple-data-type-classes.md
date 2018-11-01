---
title: Proste klasy typów danych
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: 9288ed3104d2cdf4c6938b171166de7cffd32ccf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531664"
---
# <a name="simple-data-type-classes"></a>Proste klasy typów danych

Następujące klasy hermetyzacji rysowania współrzędne, ciągi znaków i czasu i informacji o dacie, dzięki czemu wygodne użycie składni języka C++. Te obiekty są często używane jako parametry funkcji składowych klas Windows w bibliotece klas. Ponieważ `CPoint`, `CSize`, i `CRect` odpowiadają **punktu**, **rozmiar**, i **Prostokąt** struktury odpowiednio w zestawie Windows SDK Możesz użyć obiektów w ramach tych zajęć C++ wszędzie tam, gdzie możesz użyć tych konstrukcji języka C. Klasy zawierają użyteczne interfejsów za pośrednictwem ich funkcji elementów członkowskich. `CStringT` zawiera ciągi znaków dynamiczne bardzo elastyczny. `CTime`, `COleDateTime`, `CTimeSpan`, i `COleTimeSpan` reprezentują wartości godziny i daty. Aby uzyskać więcej informacji na temat tych klas, zobacz artykuł [daty i godziny](../atl-mfc-shared/date-and-time.md).

Klasy, które zaczynają się od "`COle`" są encapsulations typów danych dostarczonych przez OLE. Te typy danych może służyć w programach Windows niezależnie od tego, czy są używane inne funkcje OLE.

[CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Posiada ciągi znaków.

[Ctime —](../atl-mfc-shared/reference/ctime-class.md)<br/>
Przechowuje bezwzględne wartości godziny i daty.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Otoka dla typu automatyzacji OLE **data**. Reprezentuje wartości daty i godziny.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Przechowuje wartości względne datę i godzinę.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Posiada względne `COleDateTime` wartości, takich jak różnicę między dwoma `COleDateTime` wartości.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Przechowują pary współrzędne (x, y).

[CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Przechowuje odległość, położenie względne lub par wartości.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Zawiera współrzędne programu prostokątnych obszarów.

[CImageList](../mfc/reference/cimagelist-class.md)<br/>
Oferuje funkcje Windows listy obrazów. Listy obrazów są używane w kontrolkach listy i kontrolkach drzewa. One może również przechowywanie i archiwizowanie zestaw ten sam rozmiar mapy bitowej.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Otoka dla typu automatyzacji OLE **VARIANT**. Dane w **VARIANT**s mogą być przechowywane w wielu formatach.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Otoka dla typu automatyzacji OLE **waluty**, stałoprzecinkowa typ arytmetyczny, z 15 cyfr przed przecinkiem dziesiętnym i 4 cyfr po.

> [!NOTE]
>  `CRect`, `CSize`, i `CPoint` można używać w aplikacjach ATL lub MFC. Ponadto `CStringT` umożliwia niezależną MFC `CString`— takich jak klasy. Aby uzyskać więcej informacji na temat narzędzia udostępnione klas, zobacz [udostępnionego klasy](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../mfc/class-library-overview.md)

