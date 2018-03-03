---
title: "Proste klasy typów danych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d2b4df05d64cb97032477ca50ff4b0ce572829b9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="simple-data-type-classes"></a>Proste klasy typów danych
Następujące klasy Hermetyzowanie rysowania współrzędne, ciągi znaków i czas i informacje o dacie, dzięki czemu wygodne użycie składni języka C++. Te obiekty są często używane jako parametry do funkcji Członkowskich klas systemu Windows w bibliotece klas. Ponieważ `CPoint`, `CSize`, i `CRect` odpowiadają **punktu**, **rozmiar**, i `RECT` struktury odpowiednio w zestawie SDK systemu Windows można użyć tych obiektów C++ klas wszędzie tam, gdzie można użyć tych konstrukcji języka C. Klasy zawierają użyteczne interfejsy za pośrednictwem ich funkcje Członkowskie. `CStringT`zapewnia bardzo elastyczne ciągi dynamicznych. `CTime`, `COleDateTime`, `CTimeSpan`, i **COleTimeSpan** reprezentują wartości godziny i daty. Aby uzyskać więcej informacji na temat tych klas, zobacz artykuł [datę i godzinę](../atl-mfc-shared/date-and-time.md).  
  
 Klasy, które zaczynają się od "**COle**" są encapsulations typów danych dostarczanych przez OLE. W programów systemu Windows, niezależnie od tego, czy są używane inne funkcje OLE można używać tych typów danych.  
  
 [CStringT, klasa](../atl-mfc-shared/reference/cstringt-class.md)  
 Posiada ciągi znaków.  
  
 [Ctime —](../atl-mfc-shared/reference/ctime-class.md)  
 Przechowuje wartości bezwzględne godziny i daty.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Otoki dla typu automatyzacji OLE **data**. Reprezentuje wartości daty i godziny.  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 Zawiera względne wartości godziny i daty.  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 Przechowuje względną `COleDateTime` wartości, takich jak różnicę między dwiema `COleDateTime` wartości.  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Blokad pary współrzędne (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Przechowuje odległość, położenia lub par wartości.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Zawiera współrzędne obszary prostokątne.  
  
 [Cimagelist —](../mfc/reference/cimagelist-class.md)  
 Udostępnia funkcję listy obrazów systemu Windows. Listy obrazów są używane przez formanty listy i drzewa. One mogą służyć do przechowywania i archiwum zestaw o tej samej wielkości map bitowych.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Otoki dla typu automatyzacji OLE **VARIANT**. Dane w **VARIANT**s mogą być przechowywane w wielu formatach.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Otoki dla typu automatyzacji OLE **waluty**, stałoprzecinkowe typ arytmetyczny, 4 cyfry po i przed separatorem dziesiętnym do 15 cyfr.  
  
> [!NOTE]
>  `CRect`, `CSize`, i `CPoint` wykorzystania w aplikacji ATL ani MFC. Ponadto `CStringT` zapewnia niezależnego MFC `CString`— takich jak klasy. Aby uzyskać więcej informacji na temat klas jako narzędzia udostępnione, zobacz [udostępnionego klasy](../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../mfc/class-library-overview.md)

