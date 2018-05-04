---
title: 'CFixedStringT: Przykład z menedżerem ciąg niestandardowy | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f841124fd12497fdb4dd4b813de2d803e43ff60b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: Przykład z menedżerem ciąg niestandardowy
Przykładem menedżera niestandardowy ciąg używane przez klasę implementuje biblioteki ATL [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md)o nazwie **CFixedStringMgr**. `CFixedStringT` jest pochodną [CStringT](../atl-mfc-shared/reference/cstringt-class.md) i implementuje ciąg, który przydziela jego danych znakowych jako część `CFixedStringT` sam obiekt tak długo, jak ciąg znaków jest mniejsza od długości określonej przez **t_nChars** Parametr szablonu `CFixedStringT`. Takie podejście ciąg nie wymaga sterty, chyba, że długość ciągu przekroczy rozmiar stałego buforu. Ponieważ `CFixedStringT` jest zawsze używana sterty można przydzielić jego dane ciągu nie może używać **CAtlStringMgr** jako jego menedżera ciągu. Używa Menedżera niestandardowy ciąg (**CFixedStringMgr**), wdrożenia [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfejsu. Ten interfejs jest omówiona w [implementacji programu Menedżer ciąg niestandardowy (zaawansowane metody)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).  
  
 Konstruktor **CFixedStringMgr** przyjmuje trzy parametry:  
  
-   **pData:** wskaźnik do stałej `CStringData` struktury do użycia.  
  
-   **nChars:** maksymalną liczbę znaków `CStringData` struktury może przechowywać.  
  
-   **pMgr:** wskaźnik do `IAtlStringMgr` interfejsu "Menedżer kopii zapasowych ciąg".  
  
 Konstruktor przechowuje wartości `pData` i **pMgr** w ich zmienne Członkowskie odpowiednich (`m_pData` i **m_pMgr**). Ustawia długość buforu na zero, dostępne długość równą maksymalny rozmiar stały bufor, a liczba odwołań do -1. Wskazuje wartość liczebności referencyjnej bufor jest zablokowany i chcesz użyć tego wystąpienia **CFixedStringMgr** Menedżer ciągu.  
  
 Oznaczenie buforu, ponieważ zablokowany uniemożliwia innych `CStringT` wystąpień z zawierający odwołanie udostępnionego w buforze. Jeśli inne `CStringT` wystąpień mogli udostępniać buforu byłoby możliwe w dla buforu zawarty w `CFixedStringT` do usunięcia, podczas gdy inne ciągi zostały nadal używa buforu.  
  
 **CFixedStringMgr** jest pełnego wdrożenia `IAtlStringMgr` interfejsu. Implementacja każdej metody została omówiona osobno.  
  
## <a name="implementation-of-cfixedstringmgrallocate"></a>Implementacja CFixedStringMgr::Allocate  
 Implementacja **CFixedStringMgr::Allocate** najpierw sprawdza, czy żądany rozmiar ciągu jest mniejszy niż rozmiar buforu stałego (przechowywane w `m_pData` element członkowski). Jeśli stały bufor jest wystarczający, **CFixedStringMgr** blokuje ustalony bufor o długości zerowej. Tak długo, jak długość ciągu nie będzie zwiększać przekracza rozmiar stały bufor `CStringT` nie będzie konieczne ponowne przydzielenie buforu.  
  
 Jeśli żądany rozmiar ciągu jest większa niż stały bufor **CFixedStringMgr** przekazuje żądanie do Menedżera kopii zapasowych ciągu. Przyjmuje się, że Menedżer kopii zapasowych ciąg alokacji buforu ze stosu. Jednak przed zwróceniem bufor **CFixedStringMgr** blokuje buforu i zastępuje wskaźnika do wskaźnika menedżera ciąg buforu **CFixedStringMgr** obiektu. Dzięki temu, który próbuje ponowne przydzielenie lub wolnego buforu przez `CStringT` zostanie wywołany **CFixedStringMgr**.  
  
## <a name="implementation-of-cfixedstringmgrreallocate"></a>Implementacja CFixedStringMgr::ReAllocate  
 Implementacja **CFixedStringMgr::ReAllocate** jest bardzo podobny do stosowania **przydziel**.  
  
 Jeśli bufor przydzielany jest ustalony bufor i rozmiar żądanej buforu jest mniejszy niż stały bufor, nie jest przeprowadzane nie alokacji. Jednak jeśli bufor przydzielany nie jest stały bufor, musi być bufor przydzielony przy użyciu Menedżera kopii zapasowych. W takim przypadku służy Menedżer kopii zapasowej ponownie przydzielić buforu.  
  
 Jeśli bufor przydzielany jest ustalony bufor i nowy rozmiar buforu jest za duży dla stałego buforu **CFixedStringMgr** przydziela bufor nowego za pomocą Menedżera kopii zapasowych. Zawartość ustalony bufor są następnie kopiowane do bufor nowego.  
  
## <a name="implementation-of-cfixedstringmgrfree"></a>Implementacja CFixedStringMgr::Free  
 Implementacja **CFixedStringMgr::Free** jest zgodny ze wzorcem samej jako **przydziel** i `ReAllocate`. Jeśli bufor zwalniane jest ustalony bufor, metoda ustawia ją na zablokowanym buforu o zerowej długości. Jeśli bufor zwalniane został przydzielony przy użyciu kopii zapasowej Menedżera **CFixedStringMgr** używa kopii zapasowej Menedżera jego zwolnienia.  
  
## <a name="implementation-of-cfixedstringmgrclone"></a>Implementacja CFixedStringMgr::Clone  
 Implementacja **CFixedStringMgr::Clone** zawsze zwraca wskaźnik do tworzenia kopii zapasowej Menedżera zamiast **CFixedStringMgr** samej siebie. Wynika to z faktu, każde wystąpienie **CFixedStringMgr** może być skojarzony tylko z jednego wystąpienia `CStringT`. Wszystkie inne wystąpienia `CStringT` próbie sklonowania Menedżera należy uzyskać kopii zapasowej Menedżera zamiast tego. Jest to spowodowane Menedżera kopii zapasowej obsługuje udostępniony.  
  
## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Implementacja CFixedStringMgr::GetNilString  
 Implementacja **CFixedStringMgr::GetNilString** zwraca stałego buforu. Ze względu na zgodność Wykorzystaj **CFixedStringMgr** i `CStringT`, danego wystąpienia `CStringT` nigdy nie używa więcej niż jeden buforu naraz. W związku z tym pustego ciągu i buforu ciągu rzeczywistych nigdy nie są potrzebne w tym samym czasie.  
  
 Zawsze, gdy ustalony bufor nie jest używany, **CFixedStringMgr** gwarantuje, że zainicjowano o zerowej długości. Dzięki temu można użyć jako pustego ciągu. Jako dodatkowo `nAllocLength` elementu członkowskiego, stałego buforu ma zawsze wartość do pełnego rozmiaru stałego buforu. Oznacza to, że `CStringT` może zwiększyć się ciąg bez wywoływania [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), nawet dla pustego ciągu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** cstringt.h  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

