---
title: Klasa CStringList
ms.date: 11/04/2016
f1_keywords:
- CStringList
- AFXCOLL/CStringList
- AFXCOLL/CObList::CObList
- AFXCOLL/CObList::AddHead
- AFXCOLL/CObList::AddTail
- AFXCOLL/CObList::Find
- AFXCOLL/CObList::FindIndex
- AFXCOLL/CObList::GetAt
- AFXCOLL/CObList::GetCount
- AFXCOLL/CObList::GetHead
- AFXCOLL/CObList::GetHeadPosition
- AFXCOLL/CObList::GetNext
- AFXCOLL/CObList::GetPrev
- AFXCOLL/CObList::GetSize
- AFXCOLL/CObList::GetTail
- AFXCOLL/CObList::GetTailPosition
- AFXCOLL/CObList::InsertAfter
- AFXCOLL/CObList::InsertBefore
- AFXCOLL/CObList::IsEmpty
- AFXCOLL/CObList::RemoveAll
- AFXCOLL/CObList::RemoveAt
- AFXCOLL/CObList::RemoveHead
- AFXCOLL/CObList::RemoveTail
- AFXCOLL/CObList::SetAt
helpviewer_keywords:
- CObList [MFC], CObList
- CObList [MFC], AddHead
- CObList [MFC], AddTail
- CObList [MFC], Find
- CObList [MFC], FindIndex
- CObList [MFC], GetAt
- CObList [MFC], GetCount
- CObList [MFC], GetHead
- CObList [MFC], GetHeadPosition
- CObList [MFC], GetNext
- CObList [MFC], GetPrev
- CObList [MFC], GetSize
- CObList [MFC], GetTail
- CObList [MFC], GetTailPosition
- CObList [MFC], InsertAfter
- CObList [MFC], InsertBefore
- CObList [MFC], IsEmpty
- CObList [MFC], RemoveAll
- CObList [MFC], RemoveAt
- CObList [MFC], RemoveHead
- CObList [MFC], RemoveTail
- CObList [MFC], SetAt
ms.assetid: 310a7edb-263c-4bd2-ac43-0bfbfddc5a33
ms.openlocfilehash: 08e481f010be688fb0b9c219caa1954c9960846f
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58767278"
---
# <a name="cstringlist-class"></a>Klasa CStringList

Obsługuje listy `CString` obiektów.

## <a name="syntax"></a>Składnia

```
class CStringList : public CObject
```

## <a name="members"></a>Elementy członkowskie

Funkcje elementów członkowskich `CStringList` są podobne do funkcji elementów członkowskich klasy [CObList](../../mfc/reference/coblist-class.md). Ze względu na to podobieństwa można użyć `CObList` dokumentacji kątem specyfiki funkcja elementu członkowskiego. Po wyświetleniu `CObject` wskaźnika jako wartości zwracanej, Zastąp `CString` (nie `CString` wskaźnika). Po wyświetleniu `CObject` wskaźnika jako parametru funkcji, należy zastąpić `LPCTSTR`.

`CObject*& CObList::GetHead() const;`

na przykład przekłada się na

`CString& CStringList::GetHead() const;`

i

`POSITION AddHead( CObject* <newElement> );`

przekłada się na

`POSITION AddHead( LPCTSTR <newElement> );`

### <a name="public-constructors"></a>Konstruktory publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CObList::CObList](../../mfc/reference/coblist-class.md#coblist)|Tworzy pustą listę.|

### <a name="public-methods"></a>Metody publiczne

|Name (Nazwa)|Opis|
|----------|-----------------|
|[CObList::AddHead](../../mfc/reference/coblist-class.md#addhead)|Dodaje nagłówek listy (sprawia, że nowy główny) elementu (lub wszystkie elementy w innej listy).|
|[CObList::AddTail](../../mfc/reference/coblist-class.md#addtail)|Dodaje ogona listy (sprawia, że nowe tail) elementu (lub wszystkie elementy w innej listy).|
|[CObList::Find](../../mfc/reference/coblist-class.md#find)|Pobiera położenie elementu określonego przez wartość wskaźnika.|
|[CObList::FindIndex](../../mfc/reference/coblist-class.md#findindex)|Pobiera położenie elementu, który został określony przez indeks zaczynający się od zera.|
|[CObList::GetAt](../../mfc/reference/coblist-class.md#getat)|Pobiera element na określonej pozycji.|
|[CObList::GetCount](../../mfc/reference/coblist-class.md#getcount)|Zwraca liczbę elementów na tej liście.|
|[CObList::GetHead](../../mfc/reference/coblist-class.md#gethead)|Zwraca element główny listy (nie może być pusta).|
|[CObList::GetHeadPosition](../../mfc/reference/coblist-class.md#getheadposition)|Zwraca pozycję głównego elementu listy.|
|[CObList::GetNext](../../mfc/reference/coblist-class.md#getnext)|Pobiera następny element do wykonania iteracji.|
|[CObList::GetPrev](../../mfc/reference/coblist-class.md#getprev)|Pobiera poprzedni element do wykonania iteracji.|
|[CObList::GetSize](../../mfc/reference/coblist-class.md#getsize)|Zwraca liczbę elementów na tej liście.|
|[CObList::GetTail](../../mfc/reference/coblist-class.md#gettail)|Zwraca element tail listy (nie może być pusta).|
|[CObList::GetTailPosition](../../mfc/reference/coblist-class.md#gettailposition)|Zwraca położenie elementu tail listy.|
|[CObList::InsertAfter](../../mfc/reference/coblist-class.md#insertafter)|Wstawia nowy element po określonej pozycji.|
|[CObList::InsertBefore](../../mfc/reference/coblist-class.md#insertbefore)|Wstawia nowy element przed określonej pozycji.|
|[CObList::IsEmpty](../../mfc/reference/coblist-class.md#isempty)|Testuje pod kątem warunku lista jest pusta (Brak elementów).|
|[CObList::RemoveAll](../../mfc/reference/coblist-class.md#removeall)|Usuwa wszystkie elementy z tej listy.|
|[CObList::RemoveAt](../../mfc/reference/coblist-class.md#removeat)|Usuwa element z tej listy, który jest określony za pomocą pozycji.|
|[CObList::RemoveHead](../../mfc/reference/coblist-class.md#removehead)|Usuwa element z głowy listy.|
|[CObList::RemoveTail](../../mfc/reference/coblist-class.md#removetail)|Usuwa element z zakończeniem listy.|
|[CObList::SetAt](../../mfc/reference/coblist-class.md#setat)|Ustawia element na określonej pozycji.|

## <a name="remarks"></a>Uwagi

Wszystkie porównania są wykonywane tylko przez wartość, co oznacza, że znaki do ciągu są porównywane zamiast adresów ciągów.

`CStringList` dołącza IMPLEMENT_SERIAL — makro do obsługi serializacji i zrzucanie z jego elementów. Jeśli lista `CString` obiekty są przechowywane do archiwum, za pomocą operatora przeciążona wstawiania lub za pomocą `Serialize` funkcję członkowską, każdy `CString` element jest serializowana z osobna.

Jeśli potrzebujesz zrzutu indywidualnego `CString` elementów, należy ustawić głębokość kontekstu zrzutu 1 lub większą.

Aby uzyskać więcej informacji na temat korzystania z `CStringList`, zapoznaj się z artykułem [kolekcje](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CObject](../../mfc/reference/cobject-class.md)

`CStringList`

## <a name="requirements"></a>Wymagania

**Nagłówek:** afxcoll.h

## <a name="see-also"></a>Zobacz także

[Próbki MFC ZBIERANIE](../../overview/visual-cpp-samples.md)<br/>
[Klasa CObject](../../mfc/reference/cobject-class.md)<br/>
[Wykres hierarchii](../../mfc/hierarchy-chart.md)
