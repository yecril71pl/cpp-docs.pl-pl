---
title: 'CFixedStringT: Przykład niestandardowego Menedżera ciągów'
ms.date: 11/04/2016
helpviewer_keywords:
- CFixedStringT class, using a custom string manager
ms.assetid: 1cf11fd7-51b8-4b94-87af-02bc25f47dd6
ms.openlocfilehash: 2b6da5d4166b220ef63500d0154ab32dc72b40f4
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740705"
---
# <a name="cfixedstringt-example-of-a-custom-string-manager"></a>CFixedStringT: Przykład niestandardowego Menedżera ciągów

Biblioteka ATL zawiera przykład Menedżera niestandardowy ciąg używane przez klasę [CFixedStringT](../atl-mfc-shared/reference/cfixedstringt-class.md), co jest nazywane **CFixedStringMgr**. `CFixedStringT` jest tworzony na podstawie [CStringT](../atl-mfc-shared/reference/cstringt-class.md) i implementuje ciąg, który przydziela jej znak danych jako część `CFixedStringT` samego obiektu, tak długo, jak ciąg znaków jest mniejsza niż długość określona przez `t_nChars` parametru szablonu `CFixedStringT`. W przypadku tej metody ciąg nie musi sterty, chyba że długość ciągu przekroczy rozmiar buforu stały. Ponieważ `CFixedStringT` czy nie zawsze sterty można przydzielić jej dane ciągu nie może używać `CAtlStringMgr` jako jego menedżera ciągów. Używa ona Menedżera niestandardowy ciąg (`CFixedStringMgr`), wdrożenia [IAtlStringMgr](../atl-mfc-shared/reference/iatlstringmgr-class.md) interfejsu. Ten interfejs jest omówiona w [implementacji elementu niestandardowego Menedżera ciągów (metoda zaawansowana)](../atl-mfc-shared/implementation-of-a-custom-string-manager-advanced-method.md).

Konstruktor `CFixedStringMgr` przyjmuje trzy parametry:

- *pData:* Wskaźnik do stałej `CStringData` strukturę do użycia.

- *nChars:* Maksymalna liczba znaków `CStringData` struktura może przechowywać.

- *pMgr:* Wskaźnik do `IAtlStringMgr` interfejsu "Menedżera kopii zapasowych ciąg".

Konstruktor przechowuje wartości *pData* i *pMgr* w ich odpowiednich zmiennych (`m_pData` i `m_pMgr`). Ustawia długość buforu na zero, dostępne długość równą maksymalny rozmiar ustalony bufor, a licznik odwołań do -1. Wartość liczebności referencyjnej wskazuje rozmiar buforu jest zablokowana i korzystać z tego wystąpienia `CFixedStringMgr` jako Menedżer ds. ciąg.

Oznaczanie buforu jako zablokowaną uniemożliwia innych `CStringT` wystąpień z posiadania udostępnione odwołania do buforu. Jeśli inne `CStringT` wystąpienia zostały mogą udostępniać buforu, będzie możliwe dla buforu zawartych `CFixedStringT` do usunięcia, podczas gdy inne ciągi nadal były używane buforu.

`CFixedStringMgr` jest pełną implementację `IAtlStringMgr` interfejsu. Implementacja każdej metody została omówiona osobno.

## <a name="implementation-of-cfixedstringmgrallocate"></a>Implementacja CFixedStringMgr::Allocate

Implementacja `CFixedStringMgr::Allocate` najpierw sprawdza, czy żądany rozmiar ciągu jest mniejszy niż rozmiar buforu stałych (przechowywane w `m_pData` element członkowski). Jeśli stały bufor jest wystarczający, `CFixedStringMgr` blokuje ustalony bufor o długości zerowej. Tak długo, jak długość ciągu nie rosnąć poza rozmiar ustalony bufor `CStringT` nie zostaną ponownie przydzielić buforu.

Jeśli żądany rozmiar ciągu jest większa niż ustalony bufor `CFixedStringMgr` przekazuje żądanie do Menedżera kopii zapasowych ciągów. Menedżer kopii zapasowych ciągów jest uznawana za tę można przydzielić bufora ze sterty. Jednak przed zwróceniem tego buforu `CFixedStringMgr` blokuje buforu i zastępuje wskaźnik do buforu ciągu Menedżera wskaźnika `CFixedStringMgr` obiektu. Daje to gwarancję, który podejmie próbę ponownego przydzielenia lub zwolnienia buforu przez `CStringT` będzie wywoływać `CFixedStringMgr`.

## <a name="implementation-of-cfixedstringmgrreallocate"></a>Implementacja CFixedStringMgr::ReAllocate

Implementacja `CFixedStringMgr::ReAllocate` jest bardzo podobny do jego implementacja obiektu `Allocate`.

Jeśli rozmiar buforu, przydzielany jest ustalony bufor, rozmiar żądanej buforu jest mniejszy niż ustalony bufor odbywa się nie alokacji. Jednak jeśli bufor przydzielany nie jest ustalony bufor, musi być bufor przydzielony za pomocą Menedżera kopii zapasowych. W takim przypadku służy Menedżer kopii zapasowej ponownie przydzielić buforu.

Jeśli rozmiar buforu, przydzielany jest ustalony bufor i nowy rozmiar buforu jest za duży, aby mieściły się w limicie ustalony bufor `CFixedStringMgr` przydziela bufor nowego za pomocą Menedżera kopii zapasowych. Zawartość ustalony bufor są następnie kopiowane do bufor nowego.

## <a name="implementation-of-cfixedstringmgrfree"></a>Implementacja CFixedStringMgr::Free

Implementacja `CFixedStringMgr::Free` jest zgodna z tym samym wzorcem jako `Allocate` i `ReAllocate`. Jeśli bufor zwalniane jest ustalony bufor, metoda ustawia ją na zablokowanym bufor o zerowej długości. Jeśli bufor zwalniane został przydzielony przy użyciu Menedżera kopii zapasowych `CFixedStringMgr` używa Menedżera kopii zapasowych, aby ją bezpłatnie.

## <a name="implementation-of-cfixedstringmgrclone"></a>Implementacja CFixedStringMgr::Clone

Implementacja `CFixedStringMgr::Clone` zawsze zwraca wskaźnik do Menedżera kopii zapasowych, a nie od `CFixedStringMgr` sam. Wynika to z faktu każde wystąpienie `CFixedStringMgr` może być skojarzony tylko z jednego wystąpienia `CStringT`. Wszystkie inne wystąpienia `CStringT` próby sklonowania Menedżera pobieraj Menedżerze zapasowym. zamiast tego. Jest to spowodowane Menedżera kopii zapasowej obsługuje są udostępniane.

## <a name="implementation-of-cfixedstringmgrgetnilstring"></a>Implementacja CFixedStringMgr::GetNilString

Implementacja `CFixedStringMgr::GetNilString` zwraca stały bufor. Ze względu na zgodność indywidualną `CFixedStringMgr` i `CStringT`, danego wystąpienia programu `CStringT` nigdy nie używa więcej niż jeden buforu w danym momencie. W związku z tym ciąg zero i buforu ciągu rzeczywistą nigdy nie są potrzebne w tym samym czasie.

Zawsze, gdy ustalony bufor nie jest używany, `CFixedStringMgr` gwarantuje, że jest zainicjowany o zerowej długości. Dzięki temu może być ona używana jako ciąg wartość zero. Dodatkowym atutem `nAllocLength` członkiem ustalony bufor ma zawsze wartość do pełnego rozmiaru ustalony bufor. Oznacza to, że `CStringT` można powiększać ciąg bez wywoływania [IAtlStringMgr::Reallocate](../atl-mfc-shared/reference/iatlstringmgr-class.md#reallocate), nawet dla pustego ciągu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** cstringt.h

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią za pomocą CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
