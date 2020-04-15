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
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365398"
---
# <a name="simple-data-type-classes"></a>Proste klasy typów danych

Następujące klasy hermetyzują współrzędne rysunku, ciągi znaków oraz informacje o czasie i dacie, umożliwiając wygodne użycie składni języka C++. Obiekty te są szeroko używane jako parametry do funkcji członkowskich klas systemu Windows w bibliotece klas. Ponieważ `CPoint` `CSize`, `CRect` i odpowiadają **POINT**, **SIZE**i **RECT** struktur, odpowiednio, w Windows SDK, można używać obiektów tych klas C++ wszędzie tam, gdzie można użyć tych struktur języka C. Klasy zapewniają przydatne interfejsy za pośrednictwem ich funkcji członkowskich. `CStringT`zapewnia bardzo elastyczne dynamiczne ciągi znaków. `CTime`, `COleDateTime` `CTimeSpan`, `COleTimeSpan` i reprezentują wartości czasu i daty. Aby uzyskać więcej informacji na temat tych klas, zobacz artykuł [Data i godzina](../atl-mfc-shared/date-and-time.md).

Klasy, które zaczynają`COle`się od " " są hermetyzacjami typów danych dostarczanych przez OLE. Te typy danych mogą być używane w programach systemu Windows, niezależnie od tego, czy używane są inne funkcje OLE.

[CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Przechowuje ciągi znaków.

[Ctime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Przechowuje bezwzględne wartości czasu i daty.

[Coledatetime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Otoka dla typu automatyzacji OLE **DATE**. Reprezentuje wartości daty i godziny.

[Ctimespan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Przechowuje względne wartości czasu i daty.

[Coledatetimespan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Przechowuje `COleDateTime` wartości względne, takie `COleDateTime` jak różnica między dwiema wartościami.

[Cpoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Posiada pary współrzędnych (x, y).

[Csize](../atl-mfc-shared/reference/csize-class.md)<br/>
Utrzymuje odległość, względne pozycje lub sparowane wartości.

[Crect](../atl-mfc-shared/reference/crect-class.md)<br/>
Przechowuje współrzędne obszarów prostokątnych.

[Cimagelist](../mfc/reference/cimagelist-class.md)<br/>
Udostępnia funkcje listy obrazów systemu Windows. Listy obrazów są używane z formantami listy i formantami drzewa. Mogą być również używane do przechowywania i archiwizowania zestawu map bitowych o tym samym rozmiarze.

[Colevariant](../mfc/reference/colevariant-class.md)<br/>
Otoka dla typu automatyzacji OLE **VARIANT**. Dane w **VARIANT**S mogą być przechowywane w wielu formatach.

[Colecurrency](../mfc/reference/colecurrency-class.md)<br/>
Otoka dla typu automatyzacji OLE **CURRENCY**, typu arytmetycznego o stałym punkcie, z 15 cyframi przed przecinkiem dziesiętnym i 4 cyframi po.

> [!NOTE]
> `CRect`, `CSize`i `CPoint` są użyteczne w aplikacjach ATL lub MFC. Ponadto `CStringT` zapewnia klasy -like `CString`niezależne od MFC. Aby uzyskać więcej informacji na temat udostępnionych klas narzędziowych, zobacz [Klasy udostępnione](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../mfc/class-library-overview.md)
